SLIP 1 
1]num = int(input("Enter a number: ")) 
if num > 0: 
print("The number is positive.") 
print("This statement is inside the if block.") 
print("Program execution completed.") 

2] Q2) B .Write a python program to implement Water Jug Problem.   [20 marks] 
Programme : 
from collections import deque 
def water_jug_problem(capacity1, capacity2, target): 
visited = set() 
queue = deque() 
# Initial state 
queue.append(((0, 0), [])) 
visited.add((0, 0)) 
while queue: 
(jug1, jug2), path = queue.popleft() 
# Check goal state 
if jug1 == target or jug2 == target: 
print("\nSolution Path:") 
            for step in path: 
                print(step) 
            print("Goal State:", (jug1, jug2)) 
            return 
 
        states = [] 
 
        # Fill Jug 1 
        states.append(((capacity1, jug2), "Fill Jug 
1")) 
 
        # Fill Jug 2 
        states.append(((jug1, capacity2), "Fill Jug 
2")) 
 
        # Empty Jug 1 
        states.append(((0, jug2), "Empty Jug 1")) 
 
        # Empty Jug 2 
        states.append(((jug1, 0), "Empty Jug 2")) 
 
        # Pour Jug 1 -> Jug 2 
        amount = min(jug1, capacity2 - jug2) 
        states.append( 
            ((jug1 - amount, jug2 + amount), 
             "Pour Jug 1 -> Jug 2") 
        ) 
 
        # Pour Jug 2 -> Jug 1 
        amount = min(jug2, capacity1 - jug1) 
        states.append( 
            ((jug1 + amount, jug2 - amount), 
             "Pour Jug 2 -> Jug 1") 
        ) 
 
        for new_state, action in states: 
            if new_state not in visited: 
                visited.add(new_state) 
                queue.append( 
                    (new_state, path + [action]) 
                ) 
 
    print("No solution exists.") 
 
# Main program 
capacity1 = 4 
capacity2 = 3 
target = 2 
print("Water Jug Problem") 
print("Jug 1 Capacity:", capacity1, "litres") 
print("Jug 2 Capacity:", capacity2, "litres") 
print("Target:", target, "litres") 
water_jug_problem(capacity1, capacity2, target) 
