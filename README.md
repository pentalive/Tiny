Tiny is a small integer RPN based language created by Ron Hudson (Pentalive). 
It is a console/character type interpretive programming language, in which all statements are either 
assignments or those that print quoted strings. 

Each line consists of an integer line number, followed by any number of commands. 
Line numbers are long integer numbers. The number can have leading zeros. The commands are:

#comment to the end of line
"print this string"
[calculates an expression] stores the result into one or more variables
.

The third command is an assignment, and the fourth command ends the program. 
Multiple commands can be written on the same line. 

Escape sequences are allowed inside quoted strings (\n (newline), \e (ASCII Escape 0x1B), \t (tab), \", \\).
\e (escape) can be used to introduce ANSI escape sequences.

Expressions are written in Reverse Polish notation, and can use the following operators:

+ - * / % ^ Arithmetic (add, subtract, multiply, divide, remainder, raise to a power)
< > = Comparison (less than, greater than, equal to;
                  returns 1 for true, 0 for false)
& | ! Logical (and, or, not; uses 1 for true and 0 for false)

The stack is dynamic. 

Special Variables:
@  program counter - When this line finishes this gives the next line to execute. This variable is
valid while a line is executing, it can be use as a return address if stored on the stack

$ A stack that can store data and return addresses

Things inside "[ ]" are fetched, things outside "[ ]" are stored.

[ a 1 +] a  # increment a

Here is a short demo program:

10 "While 10 is running @ = 20\n"
20 [@] $  [40] @  # a subroutine call to line 40 storing return on the stack
30 [99]@
40 "A subroutine! " [$] @   # A one-line subroutine that only prints "A subroutine!" then returns
99 .  "End of file Sentinal and command to stop executing"


See https://esolangs.org/wiki/Tiny
