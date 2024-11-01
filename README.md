# Capstone Project-Linux Shell Scripting

## Multiplication Table Generator

This Bash script helps to generates a multiplication table for a number entered by the user. This project will help you practice using loops, handling user input and applying conditinal logic in Bash Scripting


## USAGE

   1. log into my Linux server
   2. Create multiplication.sh and run the command Vim multiplication.sh
   3. Start your shell scripting with the following command

   `#!/bin/bash`

   4. after i can make the script executable at this stage by using the following command

   `chmod +x multiplication.sh`

   5. To run the the script,i ran this command

   `./multiplication.sh`


## SCRIPT BREAKDOWN

## STEP 1: Prompting user input and validating

### Below is the summary of the command that does the following:

* Prompting User Input; The script starts by asking the user to enter a number for the multiplication table to be generated

* Validate the input number
 
* Ask if the user wants to repeat the process

* Full or Partial Table Choice;

* The user is asked whether they want a full table or a partial table

* If the user chooses full table (f) the script will generate a multiplication table starting from 1 to 10

* For Partial table, the user chooses (p), the script prompt the starting and the ending numbers of the range.

*  To validate this it has to be within 1 to 10 and the start is less than or equal to the end
    
**Find the script:**


```markdown
#!/bin/bash

read -p "Enter a number to generate its multiplication table: " number
  # Validate if the input is a valid number
if ! [[ "$number" =~ ^[0-9]+$ ]]; then
    echo "Invalid input! Please enter a valid number."
    continue
fi
 # Step 2: Ask if the user wants a full table or partial
echo "Do you want a full multiplication table (1-10) or a partial one?"
echo "f. Full (1 to 10)"
echo "p. Partial (special range)"
read -p "Enter your choice (f or p): " choice
```

![invalid-range](images/invalid-range-showing.jpg)


# STEP 2: Full Multiplication table and handling Partial choice input

### Below is the summary of the command that does the following:

* calculate the multiplication table
* it accept both **start** and **end** range 
* To validate the **start** and **end** input

**Find the script:**

```markdown
#!/bin/bash


read -p "Enter a number to generate its multiplication table: " number
  # Validate if the input is a valid number
if ! [[ "$number" =~ ^[0-9]+$ ]]; then
    echo "Invalid input! Please enter a valid number."

fi
 ### Step 2: Ask if the user wants a full table or partial
echo "Do you want a full multiplication table (1-10) or a partial one?"
echo "f. Full (1 to 10)"
echo "p. Partial (special range)"
read -p "Enter your choice (f or p): " choice

if [ "$choice" == "f" ]; then
 # Full table (1 to 10)
echo "Multiplication Table for $number"
echo "---------------------------"
for i in {1..10}; do
echo "$number x $i = $((number * i))"
done
elif [ "$choice" == "p" ]; then
 # Partial table, ask for start and end range
read -p "Enter the start of the range: " start
read -p "Enter the end of the range: " end
 # Validate if the start and end inputs are valid numbers and if start is less than or equal to end
 if ! [[ "$start" =~ ^[0-9]+$ ]] || ! [[ "$end" =~ ^[0-9]+$ ]] || [ "$start" -gt "$end" ]; then
echo "Invalid range! Showing full table (1-10) instead."
start=1
end=10
 fi
fi


```
The image below shows the full multiplication result

![full-table](images/full-multiplication-table.jpg)


## STEP 3: Handling Multiplication table for partial choice (p)

### Below is the summary of the command that does the following:

* calculate the partial multiplication table
* Ask if the user wants to repeat the process

**Find the script:**

```markdown
#!/bin/bash
while true; do
  # Step 1: Ask the user for a number
  read -p "Enter a number to generate its multiplication table: " number
  # Validate if the input is a valid number
  if ! [[ "$number" =~ ^[0-9]+$ ]]; then
    echo "Invalid input! Please enter a valid number."
    continue
  fi
  # Step 2: Ask if the user wants a full table or partial
  echo "Do you want a full multiplication table (1-10) or a partial one?"
  echo "f. Full (1 to 10)"
  echo "p. Partial (special range)"
  read -p "Enter your choice (f or p): " choice
  if [ "$choice" == "f" ]; then
    # Full table (1 to 10)
    echo "Multiplication Table for $number"
    echo "---------------------------"
    for i in {1..10}; do
      echo "$number x $i = $((number * i))"
    done
  elif [ "$choice" == "p" ]; then
    # Partial table, ask for start and end range
    read -p "Enter the start of the range: " start
    read -p "Enter the end of the range: " end
    # Validate if the start and end inputs are valid numbers and if start is less than or equal to end
    if ! [[ "$start" =~ ^[0-9]+$ ]] || ! [[ "$end" =~ ^[0-9]+$ ]] || [ "$start" -gt "$end" ]; then
      echo "Invalid range! Showing full table (1-10) instead."
      start=1
      end=10
    fi
    # Generate partial table
    echo "Multiplication Table for $number (from $start to $end)"
    echo "-----------------------------------"
    for ((i=start; i<=end; i++)); do
      echo "$number x $i = $((number * i))"
    done
  else
    echo "Invalid choice! Please enter f for full or p for partial."
    continue
  fi
  # Step 6: Ask if the user wants to repeat the process
  read -p "Do you want to generate another table? (y/n): " repeat
  if [[ "$repeat" != "y" ]]; then
    echo "Exiting the program."
    break
  fi
done
```


The image below shows the entire result of this script:


 ![complete-table](images/complete-multiplication-output.jpg)

From the above output,
* I enhanced user interaction 
* I entered a number to generate the Full multiplication table
* Also for partial range
* Then i tried invalid range

