# C## Programming Language
### v0.5 Beta 1

A simple compiled programming language in the C family, inspired by Scratch.
C## compiles to x86-64 and ARM64 assembly and produces real native executables on Linux.

## Building the Compiler

Requires: `gcc`, `as` (GNU assembler), `ld`

```bash
gcc -o cmm chh_compiler.c
```

## Compiling a C## Program

```bash
./cmm hello.chh hello.s   # compile to assembly
as -o hello.o hello.s     # assemble
ld -o hello hello.o       # link
./hello                   # run
```

## Full Language Reference

### Output & Input
```c
say("Hello, World!");              // print string
say("Score: " + score);           // print with variable
say("a=" + a + " b=" + b);        // join multiple parts
ask("What is your name? ");        // prompt user
say("Hello " + answer + "!");     // use the answer
```

### Variables
```c
set x to 5;              // integer variable
set name to "Alice";     // string variable
set x to x + 10;         // expressions
change x by 3;           // add to variable (negative to subtract)
```

### Math Operators
```c
set x to 10 + 5;
set x to 10 - 3;
set x to 4 * 4;
set x to 10 / 2;
set x to 10 mod 3;
```

### Math Functions
```c
set x to abs(-5);            // absolute value → 5
set x to sqrt(25);           // square root → 5
set x to power(2, 8);        // 2^8 → 256
set x to min(3, 7);          // minimum → 3
set x to max(3, 7);          // maximum → 7
set x to floor(x);           // round down
set x to ceil(x);            // round up
set x to round(x);           // round to nearest
set x to pick random 1 to 10; // random number
```

### String Operations
```c
set name to "Alice";
set l to length of name;      // string length
if name = "Alice" {           // string comparison
    say("hello Alice!");
}
```

### If Statements
```c
if x = 5 then {
    say("x is 5!");
}

if x > 10 {
    say("big!");
} else {
    say("small!");
}

if x >= 10 and x <= 20 {
    say("between 10 and 20");
}

if not x = 99 {
    say("not 99");
}

// Operators: = < > <= >= and or not
```

### Loops
```c
repeat 10 times {
    say("hello!");
}

repeat until x = 10 {
    change x by 1;
}

forever {
    say("looping...");
}
```

### Break & Continue
```c
repeat 10 times {
    change i by 1;
    if i = 5 {
        break;      // exit loop
    }
    if i = 3 {
        continue;   // skip to next iteration
    }
    say(i);
}
```

### Timing & Control
```c
wait 2;              // wait 2 seconds
wait until x = 5;   // wait until condition is true
stop;                // exit the program
```

### Lists
```c
add 100 to scores;
add 200 to scores;
add 300 to scores;
say(length of scores);          // 3
say(item 2 of scores);          // 200
replace 2 of scores with 999;
delete 1 of scores;
insert 42 at 1 of scores;

if scores contains 999 {
    say("found it!");
}
```

### Functions
```c
define greet(name) {
    say("Hello " + name + "!");
}

define add(a, b) {
    set result to a + b;
    say(result);
}

define main() {
    greet("Alice");
    add(5, 3);
}
```

### File I/O
```c
writefile("data.txt", "hello!");
set contents to readfile("data.txt");
say(contents);
```

### Comments
```c
// this is a comment
```

## Example: FizzBuzz
```c
define main() {
    set i to 1;
    repeat 20 times {
        if i mod 15 = 0 {
            say("FizzBuzz");
        }
        if i mod 3 = 0 and not i mod 15 = 0 {
            say("Fizz");
        }
        if i mod 5 = 0 and not i mod 15 = 0 {
            say("Buzz");
        }
        if not i mod 3 = 0 and not i mod 5 = 0 {
            say(i);
        }
        change i by 1;
    }
}
```

## Example: Guessing Game
```c
define main() {
    set secret to pick random 1 to 100;
    set guess to 0;
    set tries to 0;

    say("Guess a number between 1 and 100!");

    repeat until guess = secret {
        ask("Your guess: ");
        set guess to answer;
        change tries by 1;

        if guess < secret {
            say("Too low!");
        }
        if guess > secret {
            say("Too high!");
        }
    }

    say("Correct! You got it in " + tries + " tries!");
}
```