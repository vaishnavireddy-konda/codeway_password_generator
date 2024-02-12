# codeway_password_generator
import tkinter as tk
import random
import string

def generate_password():
    try:
        length = int(entry_length.get())
        if length <= 0:
            result_label.config(text="Please enter a positive integer for the password length.")
            return
        characters = string.ascii_letters + string.digits + string.punctuation
        password = ''.join(random.choice(characters) for _ in range(length))
        result_label.config(text="Generated Password: " + password)
    except ValueError:
        result_label.config(text="Please enter a valid integer for the password length.")

root = tk.Tk()
root.title("Password Generator")
root.configure(bg="red")
length_label = tk.Label(root, text="Enter password length:",bg="#008080",fg="white")
length_label.grid(row=0, column=0, padx=5, pady=5)

entry_length = tk.Entry(root, width=10)
entry_length.grid(row=0, column=1, padx=5, pady=5)

generate_button = tk.Button(root, text="Generate Password", command=generate_password, bg="#008080", fg="white")
generate_button.grid(row=1, columnspan=2, padx=5, pady=5)

result_label = tk.Label(root, text="", bg="#f0f0f0")
result_label.grid(row=2, columnspan=2, padx=5, pady=5)

root.mainloop()
