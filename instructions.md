# Instructions

<details>
  <summary>
    💡 REPL/PyCharm Guide
  </summary>

  - To toggle commenting, highlight the line(s) and press Ctrl + /
  - To move a statement or block of statements one indent to the right, highlight the statement(s)  press Tab
  - To move a statement or block of statements one indent to the left, highlight the statement(s)  press Shift+Tab
  - Avoid using backspaces or spaces to remove or place indents
  - REPL Comments
    - To ask the instructor a code question, highlight the line(s) of code and press Alt + / and type in your question/issue/comment and click on collapse
    - To view comments placed by the instructor click on the comment icon at the end of any highlighted code
    - If your issue is resolved, click on Resolve to remove the comment
</details>


<details>
  <summary>
    Assignment Instructions
  </summary>

- In this assignment we manage product data using complex dictionary
- Each product has three data elements - Name, Price, Quantity
- That data will be stored in a dictionary with keys name, price, qty
- All such dictionaries for each product is stored in a dictionary whose keys will be the product ID we calculate for each product
</details>


## Start Working

<details>
  <summary>
    ✅ Create a new PyCharm project
  </summary>

  - Create a new PyCharm project in a folder of your choice
  - Create a Python file - main.py
  - Inside the project create a new folder **cw07**
  - Create files dict_functions.py and validations.py
  - Download [products.bin](https://github.com/suchialex/CINS3002-CW07/blob/main/products.bin)
  - If needed, download [suchi_pretty_print](https://github.com/suchialex/pretty-print/blob/main/suchi_pretty_print.py) 
</details>

<details>
  <summary>
    ✅ Copy code from cw06
  </summary>

  - Copy main.py
  - Copy the code in validations.py from CW06
  - Change the import statement in main.py to use dict_functions module
</details>

## In dict_functions.py

<details>
  <summary>
    ✅ Define product_operations
  </summary>

  - For now place the keyword pass
</details>

<details>
  <summary>
    ✅ Define function file_to_dictionary()
  </summary>
  
  - It accepts no parameters
  - It returns the products dictionary
  - In the function body,
    - Check if there is any data in product.bin inside the cw07 folder
      - if no data, then return an empty dictionary
    - Using context manager, unpickle the contents of the file products.bin to a dictionary and store in a variable of your choice
    ⏩ Refer to 9-11
    - Print this dictionary and check contents (you may comment it out after)
    - Return this dictionary
</details>


<details>
  <summary>
    ✅ Modify employee_operations() function
  </summary>
  
  - Call the file_to_dictionary() after the pass statement
  - Print the returned dictionary
  - 📜 Execute your code to check if the dictionary is printed correctly, you may use suchi_print
</details>

## In validations.py

<details>
  <summary>
    ✅ Define get_next_prodid_dict() function
  </summary>
  
  Parameters: Dictionary<br>
  Returns: Integer<br>
  Description: This functions finds the max product ID in the dictionary and adds 1 to it and returns the next product ID in a integer format<br>

<details>
  <summary>
    🔑 Code Logic:
  </summary>

  - If dictionary is empty, return 1001 (integer, not a string)
  - Get the dictionary keys of the products dictionary and store in a variable ⏩ Refer to 9-9f
  - Get the max element from that ⏩ Refer to 7-15
  - Add 1 to the max key and return it
</details>

</details>

## In dict_functions.py

<details>
  <summary>
    ✅ Define add_product() function
  </summary>

Parameters: Dictionary  
Returns: Dictionary  
Description: We add a new product to the dictionary and return the modified dictionary.

<details>
  <summary>
    🔑 Code Logic:
  </summary> 

  - Product ID is obtained from function call to get_next_prodid_dict() 
  - Name is obtained from function calls to validate_product_name() 
  - Price is obtained from a function call to validate_price()
  - Quantity is obtained from a function call to validate_qty()
  - Using all these values create a dictionary named `new_product` with the  key/value pairs  
  "name" -> Name  
  "price" -> Price  
  "qty" -> Quantity

  - Now, to the products dictionary add a new key/value pair
    - key is the calculated product ID and
    - value is new_product dictionary
    - ⏩ Refer to 9-4a
  - Print `Added Product`
  - Return products dictionary
</details>

</details>


<details>
  <summary>
    ✅ Call add_product()
  </summary>
  
  - In product_operations() function, after the file_to_dictionary() call add_product() by passing products as the argument
</details>

<details>
  <summary>
    ✅ Define lookup_product()
  </summary>

  Parameters: Dictionary, Integer - (product dictionary, product_id)  
  Returns: Boolean (True if employee is found, False if not found)  
  Description: We check if the product ID is present in the product dictionary and if found, print all the available data elements for that product in a pretty format like this  
Name: Samsung Headset  
Price: 24.99  
Quantity: 15  

<details>
  <summary>
    🔑 Code Logic:
  </summary> 

  - Convert the user provided product ID to integer (this might raise exception if user enteres non-numeric values, so use exception handling)
  - Using in operator check if the product ID is in the dictionary   ⏩ Refer to 9-6c
  - If yes,
    - print the name, price and quantity
    - return True
  - Else
    - print `Product Not Found`
    - return False

🚩 Important: Before you print each data element, make sure that key exists for that product. ⏩ Refer to 9-6c or use the get method with the second parameter
</details>
</details>

<details>
  <summary>
    ✅ Call lookup_product() after add_product()
  </summary>

  - Get user input for the product ID that needs to be looked up
  - Call lookup_product with the products dictionary and the above product ID as arguments
  - Test your code with the most recently added product
</details>


<details>
  <summary>
    ✅ Define function modify_name()
  </summary>

  Parameters: Dictionary  
  Returns: Dictionary  
  Description: We use the lookup_product function to see if the product ID is present in our product dictionary, if yes, we get the new name from the user and modify the dictionary appropriately
  
<details>
  <summary>
    🔑 Code Logic:
  </summary>
  
  - Ask user to provide the product ID to modify name
  - Call the function lookup_product using products dictionary and the above product ID as arguments and store returned value in a variable called found
  - if found is true
    - we ask the user to give us a valid name using a call to the validate_produc_name
    - Then we find the appropriate dictionary element and modify it  ⏩ Refer to 9-4a
    - 🚩 Do not forget to change the product id to integer
    - Print `Name Modified Successfully`
  - Outside if block, return the products (optional if you are using the same name for the dictionary)
</details>
</details>


<details>
  <summary>
    ✅ Call modify_name() after lookup_product()
  </summary>

  - Call modify_name using the products dictionary as an argument
  - Print the products dictionary (you may comment it out later)
  - Test your code and make sure product name is being modified correctly
</details>


<details>
  <summary>
    ✅ Same for modify_price, modify_quantity
  </summary>

  - Do the same steps as above for modifying price and quantity
</details>


<details>
  <summary>
    ✅ Define display_products()
  </summary>

  Parameters: Dictionary  
  Returns: None  
  Description: We use a for loop to go over the product dictionary and print all data elements in a tabular format

<details>
  <summary>
    🔑 Code Logic:
  </summary>

  - Start a for loop to go over the product dictionary's keys
    - Get each product dictionary using the loop variable
    - For example each_product = <product dictionary>[<loop_variable>]
    - For example, product name would be  `each_product.get("name", "-")`
    - Do the same for other data elements, price and quantity
    - Product ID is the loop variable
  - Display all these values in a tabular format
  - You may choose column widths and alignment to fit your data

</details>

</details>


<details>
  <summary>
    ✅ Call  display_products()
  </summary>

  - Call display_products() with the products dictionary as argument
  - Test your code
</details>


<details>
  <summary>
    ✅ Define delete_product()
  </summary>

  Parameters: Dictionary  
  Returns: Dictionary  
  Description: We use the lookup_product function to see if the product ID is present in our product dictionary, if yes, we delete that product from the dictionary
  
<details>
  <summary>
    🔑 Code Logic:
  </summary>
  
  - Ask user to provide the product ID to delete
  - Call the function lookup_product using products dictionary and the above product ID as arguments and store returned value in a variable called found
  - if found is true
    - Delete the appropriate dictionary element  ⏩ Refer to 9-6a
    - 🚩 Do not forget to change the product id to integer
    - Print `Product Deleted Successfully`
  - Outside if block, return the employees (otpional if same named is used for the dictionary)
</details>
</details>



<details>
  <summary>
    ✅ Call  delete_product()
  </summary>

  - Call delete_product() with the products dictionary as argument
  - Print the products dictionary to test (you may comment it out later)
</details>


<details>
  <summary>
    ✅ Define dictionary_to_file function
  </summary>

  Parameters: Dictionary  
  Return: None 

  - Pickle the products dictionary to products.bin file in the products folder  Refer to ⏩ 9-10

</details>

<details>
  <summary>
    ✅ Call  dictionary_to_file()
  </summary>

  - Call dictionary_to_file() passing the products dictionary as argument
</details>

<details>
  <summary>
    ✅ Complete product_operations() function
  </summary>

  - Call the file_to_dictionary() function
  - Inside a while loop that runs **until user presses 0**, print menu of options, get user's choice and inside the if-elif-else blocks calls the appropriate functions
  - Outside the while loop call dictionary_to_file() function
  - Also make sure add_product is in a while loop until user presses **y or Y**
</details>


## Copy code to replit

<details>
  <summary>
    ✅ Copy code to replit
  </summary>
  
  - Copy the contents of validations.py and dict_functions.py to replit under folder cw07
  - Comment out the existing import statement and code in main function body
  - Copy and paste the import statement and code from main.py in your PyCharm Project
  - Submit the URL on Canvas assignment
</details>
