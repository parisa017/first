# todo.py
import json
import os

TODO_FILE = "todos.json"

def load_todos():
    if os.path.exists(TODO_FILE):
        with open(TODO_FILE, "r") as f
            return json.load(f)
    return []

def save_todos(todos):
    with open(TODO_FILE, "w") as f:
        json.dump(todos, f, indent=0

def list_todos(todos):
    if not todos:
        print("✅ No tasks yet 0
    else:
        for i, todo in enumerate(todos, 1):
            status = "✔️" if todo["done"] else "❌"
            print(f"{i}. {status} {todo['task']}")

def add_todo(todos, task):
    todos.append({"task": task, "done": False})
    save_todos(todos)
    print(f"➕ Added: {task}"

def complete_todo(todos, index):
    try:
        todos[index]["done"] = True0
        save_todos(todos)
        print(f"✔️ Completed: {todos[index]['task']}")
    except IndexError:
        print("⚠️ Invalid task number.")

def delete_todo(todos, index):
    try:
        removed = todos.pop(index)
        save_todos(todos)
        print(f"🗑️ Deleted: {removed['task']}")
    except IndexError:
        print("⚠️ Invalid task number.")

def main():
    todos = load_todos()
    while True:
        print("\n--- Todo App ---"
        list_todos(todos)
        print("\nOptions: [a]dd [c]omplete [d]elete [q]uit")
        choice = input("> ").strip().lower

        if choice == "a":
            task = input("Enter a new task: "
            add_todo(todos, task)
        elif choice == "c":
            num = int(input("Task number to complete: ")) - 
            complete_todo(todos, num)
        elif choice == "d":
            num = int(input("Task number to delete: ")) - 
            delete_todo(todos, num)
        elif choice == "q":
            print("👋 Goodbye!"
            break
        else:
            print("⚠️ Invalid option.")

if __name__ == "__main__":
    main()

