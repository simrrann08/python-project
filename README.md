from tkinter import *

# Function to calculate total and generate receipt
def calculate_and_show():
    coffee = coffee_qty.get() * 50
    tea = tea_qty.get() * 30
    sandwich = sandwich_qty.get() * 70
    total = coffee + tea + sandwich

    # Update total label
    total_label.config(text=f"Total: ₹{total}")

    # Generate receipt
    receipt = f"Coffee x {coffee_qty.get()} = ₹{coffee}\n" \
              f"Tea x {tea_qty.get()} = ₹{tea}\n" \
              f"Sandwich x {sandwich_qty.get()} = ₹{sandwich}\n" \
              f"-----------------\nTotal: ₹{total}"
    receipt_text.delete(1.0, END)  # Clear previous receipt
    receipt_text.insert(END, receipt)

# Create the main window
root = Tk()
root.title("Café Management")
root.geometry("500x600")
root.config(bg="#f2e3c6")  # Set background color

# Variables for item quantities
coffee_qty = IntVar()
tea_qty = IntVar()
sandwich_qty = IntVar()

# Header label
Label(root, text="Café Menu", font=("Arial", 18), bg="#f2e3c6").grid(row=0, column=0, columnspan=2, pady=10)

# Item and Quantity Headers
Label(root, text="Item", font=("Arial", 14, "bold"), bg="#f2e3c6").grid(row=1, column=0, padx=20, pady=5, sticky=W)
Label(root, text="Quantity", font=("Arial", 14, "bold"), bg="#f2e3c6").grid(row=1, column=1, padx=20, pady=5)

# Menu items with entry fields for quantity
Label(root, text="Coffee (₹50)", font=("Arial", 14), bg="#f2e3c6").grid(row=2, column=0, padx=20, pady=5, sticky=W)
Entry(root, textvariable=coffee_qty, width=5).grid(row=2, column=1, padx=20, pady=5)

Label(root, text="Tea (₹30)", font=("Arial", 14), bg="#f2e3c6").grid(row=3, column=0, padx=20, pady=5, sticky=W)
Entry(root, textvariable=tea_qty, width=5).grid(row=3, column=1, padx=20, pady=5)

Label(root, text="Sandwich (₹70)", font=("Arial", 14), bg="#f2e3c6").grid(row=4, column=0, padx=20, pady=5, sticky=W)
Entry(root, textvariable=sandwich_qty, width=5).grid(row=4, column=1, padx=20, pady=5)

# Button to calculate and show receipt
Button(root, text="Calculate & Show Receipt", command=calculate_and_show).grid(row=5, column=0, columnspan=2, pady=10)

# Display total and receipt
total_label = Label(root, text="Total: ₹0", font=("Arial", 14), bg="#f2e3c6")
total_label.grid(row=6, column=0, columnspan=2, pady=10)

receipt_text = Text(root, height=8, width=30)
receipt_text.grid(row=7, column=0, columnspan=2, pady=10)

# Run the application
root.mainloop()
