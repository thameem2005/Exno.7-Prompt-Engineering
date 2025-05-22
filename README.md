# Exno.7 - Prompt Engineering


### Aim:
To develop a prompt-based application tailored to personal needs, fostering creativity and practical problem-solving skills while leveraging the capabilities of large language models.

### Objective:
The objective of this exercise is to demonstrate the development of a prompt-based application using ChatGPT. The application will focus on organizing daily tasks and will showcase the progression from simple to more advanced prompt designs, illustrating how to harness the capabilities of a large language model effectively.

---

## Algorithm: 

### Step 1: Define the Problem
The first step is to clearly define the problem and scope of the application. The goal here is to create a task management system where users can input their daily tasks, and the model will help them organize and prioritize those tasks in a structured manner.

#### Key functionalities:
1. **Task Input**: Allow the user to input a list of tasks.
2. **Task Categorization**: Automatically categorize tasks based on types (e.g., work, personal, groceries).
3. **Prioritization**: Suggest priorities based on deadlines or importance.
4. **Task Summary**: Provide a summary of the day's tasks, including a suggested timeline.

### Step 2: Create Simple Prompts
Start with basic prompts to help the user input tasks and receive simple responses.

#### Sample Prompt 1:
```plaintext
"Please list your tasks for today."
```

### Step 3: Implement Categorization
Now that the user has input their tasks, use a more advanced prompt to categorize them into predefined groups such as work, personal, and others.

#### Sample Prompt 2:
```plaintext
"Please categorize these tasks into work, personal, and miscellaneous categories. Tasks: [task list]"
```

### Step 4: Task Prioritization
Add a prompt that asks the model to prioritize the tasks based on deadlines or importance.

#### Sample Prompt 3:
```plaintext
"Please prioritize the following tasks based on their urgency and importance: [task list]. Include estimated time for each task."
```

### Step 5: Suggest a Task Plan
Use a complex prompt to generate a suggested plan for completing the tasks, including timing and recommended order.

#### Sample Prompt 4:
```plaintext
"Please create a task plan for the following tasks, suggesting the best order to complete them, taking into account deadlines and estimated durations. Tasks: [task list]."
```

### Step 6: Feedback and Optimization
Based on user feedback, optimize and refine the prompts to provide better task management, suggestions, and improvements.


## Code Implementation:
We will now implement a simple Python application using OpenAI's GPT-3/ChatGPT model. This app will use the prompt-based approach to manage and organize daily tasks.

### Prerequisites:
- Python 3.x
- OpenAI API Key (required for using the GPT model)

### Installing OpenAI Python Library:
To interact with the OpenAI API, we first need to install the OpenAI Python library:

```bash
pip install openai
```

### Code Implementation

```python
import openai

# Function to initialize OpenAI API
def initialize_openai():
    openai.api_key = "YOUR_OPENAI_API_KEY"

# Function to create prompt-based tasks management
def organize_tasks(tasks):
    # Simple task input
    prompt_input = f"Please list your tasks for today: {tasks}"

    # Categorizing tasks
    prompt_categorization = f"Please categorize these tasks into work, personal, and miscellaneous categories: {tasks}"

    # Prioritizing tasks
    prompt_prioritization = f"Please prioritize the following tasks based on their urgency and importance: {tasks}. Include estimated time for each task."

    # Task plan suggestion
    prompt_plan = f"Please create a task plan for the following tasks, suggesting the best order to complete them, taking into account deadlines and estimated durations: {tasks}"

    return prompt_input, prompt_categorization, prompt_prioritization, prompt_plan

# Function to call OpenAI API with prompts
def call_openai_api(prompt):
    response = openai.Completion.create(
        engine="text-davinci-003",  # You can use "gpt-3.5-turbo" or another model
        prompt=prompt,
        max_tokens=150,
        n=1,
        stop=None,
        temperature=0.7
    )
    return response.choices[0].text.strip()

# Main function to organize tasks using ChatGPT
def main():
    # Example tasks list (in real-world use, this would be input by the user)
    tasks = [
        "Finish work report",
        "Buy groceries",
        "Call the dentist",
        "Prepare for the meeting",
        "Pick up dry cleaning"
    ]
    
    initialize_openai()
    
    # Generate the prompts
    prompt_input, prompt_categorization, prompt_prioritization, prompt_plan = organize_tasks(tasks)
    
    # Get responses from OpenAI API
    response_input = call_openai_api(prompt_input)
    response_categorization = call_openai_api(prompt_categorization)
    response_prioritization = call_openai_api(prompt_prioritization)
    response_plan = call_openai_api(prompt_plan)
    
    # Display the results
    print("Input Tasks: ", response_input)
    print("\nCategorized Tasks: ", response_categorization)
    print("\nPrioritized Tasks: ", response_prioritization)
    print("\nSuggested Task Plan: ", response_plan)

if __name__ == "__main__":
    main()
```

## Explanation of Code:

1. **initialize_openai()**: This function initializes the OpenAI API using the provided API key.
   
2. **organize_tasks()**: This function generates four different prompts to manage tasks: one for input, one for categorization, one for prioritization, and one for task planning.
   
3. **call_openai_api()**: This function sends the generated prompts to the OpenAI API and retrieves the response.
   
4. **main()**: This is the main function where tasks are input as a list. It calls the `organize_tasks()` function to generate the prompts and then calls the API with those prompts. The responses are then printed out in a structured way.

---

## Result:

Upon running the program, the system should output:

1. **Input Tasks**: A list of tasks the user has provided.
   
2. **Categorized Tasks**: Tasks categorized into work, personal, and miscellaneous.
   
3. **Prioritized Tasks**: Tasks prioritized by urgency and importance.
   
4. **Suggested Task Plan**: A structured plan for completing the tasks, including suggested timing.

---

## Conclusion:

The prompt-based task management system works by leveraging ChatGPT's ability to understand and organize human language. By designing effective prompts, it is possible to automate the process of categorizing, prioritizing, and scheduling tasks, making it an efficient tool for managing daily activities.

The solution can be further enhanced by integrating additional features like setting reminders, tracking progress, or allowing dynamic task inputs through a user interface.
