# umc0mission1
const todoInput = document.getElementById('todo-input');
const todoList = document.getElementById('todo-list');
const doneList = document.getElementById('done-list');

// 할 일 추가 함수
function addTodo(text) {
  if (!text.trim()) return; // 빈문자열 무시

  const li = document.createElement('li');
  li.textContent = text;

  // 완료 버튼
  const doneBtn = document.createElement('button');
  doneBtn.textContent = '완료';
  doneBtn.addEventListener('click', () => {
    todoList.removeChild(li);     // 해야 할 일 목록에서 삭제
    addDone(text);                // 해낸 일 목록에 추가
  });

  li.appendChild(doneBtn);
  todoList.appendChild(li);
}

// 해낸 일 추가 함수
function addDone(text) {
  const li = document.createElement('li');
  li.textContent = text;

  // 삭제 버튼
  const deleteBtn = document.createElement('button');
  deleteBtn.textContent = '삭제';
  deleteBtn.addEventListener('click', () => {
    doneList.removeChild(li);  // 해낸 일 목록에서 삭제
  });

  li.appendChild(deleteBtn);
  doneList.appendChild(li);
}

// Enter 입력 이벤트
todoInput.addEventListener('keydown', (event) => {
  if (event.key === 'Enter') {
    addTodo(todoInput.value);
    todoInput.value = '';  // 입력창 초기화
  }
});
