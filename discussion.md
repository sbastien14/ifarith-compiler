# Discussion and Reflection


The bulk of this project consists of a collection of five
questions. You are to answer these questions after spending some
amount of time looking over the code together to gather answers for
your questions. Try to seriously dig into the project together--it is
of course understood that you may not grasp every detail, but put
forth serious effort to spend several hours reading and discussing the
code, along with anything you have taken from it.

Questions will largely be graded on completion and maturity, but the
instructors do reserve the right to take off for technical
inaccuracies (i.e., if you say something factually wrong).

Each of these (six, five main followed by last) questions should take
roughly at least a paragraph or two. Try to aim for between 1-500
words per question. You may divide up the work, but each of you should
collectively read and agree to each other's answers.

[ Question 1 ] 

For this task, you will three new .irv programs. These are
`ir-virtual?` programs in a pseudo-assembly format. Try to compile the
program. Here, you should briefly explain the purpose of ir-virtual,
especially how it is different than x86: what are the pros and cons of
using ir-virtual as a representation? You can get the compiler to to
compile ir-virtual files like so: 

racket compiler.rkt -v test-programs/sum1.irv 

(Also pass in -m for Mac)

IR-Virtual is a step in the compilation process that represents assembly code with virtual registers. Virtual registers are like placeholders for actual registers that will be used in the final assembly x86 code. The purpose of this stage is to simplify the compilation process by reducing the complexity of dealing with actual hardware registers and memory locations. During this stage, the compiler generates instructions that operate on these virtual registers. These instructions mimic the behavior of the target architecture's assembly language but abstract away the specific details of register allocation and memory management. For example, instead of directly using physical registers like "rax" or "rbx," the compiler may use generic register names like "r1" or "r2" to represent virtual registers. The advantage of using virtual registers is that it simplifies the subsequent stages of the compilation process, such as optimization and code generation. Additionally, it allows the compiler to focus on generating correct and efficient code without being tied to the limitations of a specific hardware architecture. In summary, the IR-Virtual stage serves as an intermediate representation of the IfArith's logic and control flow, expressed in terms of virtual registers, before being translated into actual assembly code in later stages of the compilation pipeline.

[ Question 2 ] 

For this task, you will write three new .ifa programs. Your programs
must be correct, in the sense that they are valid. There are a set of
starter programs in the test-programs directory now. Your job is to
create three new `.ifa` programs and compile and run each of them. It
is very much possible that the compiler will be broken: part of your
exercise is identifying if you can find any possible bugs in the
compiler.

For each of your exercises, write here what the input and output was
from the compiler. Read through each of the phases, by passing in the
`-v` flag to the compiler. For at least one of the programs, explain
carefully the relevance of each of the intermediate representations.

Test cases:

Unfortunately, our group was having trouble to get the compiler to run on any sort of test file. We were able to run the compiler.rkt file, but whenever we'd run the lp line of code, it would say that our excutable file was not found. Which is strange because we're seeing the .o file in our directory. 

However, with our knowledge of compilers, executable files, and the fibonacci sequence, we expect that when the test is run from main, it will assign the number 8 to one of the registers, pass that register as the parameter for the fibonacci function and the recursively calculate the 8th fibonacci number. Afterwards, it will print that result. 

For this question, please add your `.ifa` programs either (a) here or
(b) to the repo and write where they are in this file. 
The .ifa programs are in the test-programs directory and are called test1.ifa, test2.ifa, and test3.ifa.

[ Question 3 ] 

Describe each of the passes of the compiler in a slight degree of
detail, using specific examples to discuss what each pass does. The
compiler is designed in series of layers, with each higher-level IR
desugaring to a lower-level IR until ultimately arriving at x86-64
assembler. Do you think there are any redundant passes? Do you think
there could be more?

In answering this question, you must use specific examples that you
got from running the compiler and generating an output.

Once again, we couldn't get the compiler to work, so we don't have any specific examples to give you. However, we think there are enough layers and that none should be added or taken away. The first layer defines all the terms in our language, the second tells the compiler what to do for each term in our language, the third layer turns the compiler we made into abstract normal form so the compiler built in on our devices is able to understand the compiler we've just created, in the fourth step the function creates registers that are used in any unix based operating system, and then finally in step 5 we're able to take the ANF and use the registers we created in step 4 to run our program. If we were to remove any of the steps, the compiler wouldn't work with a unix based OS. Adding anymore steps would just be redundent and unnecessary. 

[ Question 4 ] 

This is a larger project, compared to our previous projects. This
project uses a large combination of idioms: tail recursion, folds,
etc.. Discuss a few programming idioms that you can identify in the
project that we discussed in class this semester. There is no specific
definition of what an idiom is: think carefully about whether you see
any pattern in this code that resonates with you from earlier in the
semester.

[ Question 5 ] 

In this question, you will play the role of bug finder. I would like
you to be creative, adversarial, and exploratory. Spend an hour or two
looking throughout the code and try to break it. Try to see if you can
identify a buggy program: a program that should work, but does
not. This could either be that the compiler crashes, or it could be
that it produces code which will not assemble. Last, even if the code
assembles and links, its behavior could be incorrect.

To answer this question, I want you to summarize your discussion,
experiences, and findings by adversarily breaking the compiler. If
there is something you think should work (but does not), feel free to
ask me.

Your team will receive a small bonus for being the first team to
report a unique bug (unique determined by me).

[ High Level Reflection ] 

In roughly 100-500 words, write a summary of your findings in working
on this project: what did you learn, what did you find interesting,
what did you find challenging? As you progress in your career, it will
be increasingly important to have technical conversations about the
nuts and bolts of code, try to use this experience as a way to think
about how you would approach doing group code critique. What would you
do differently next time, what did you learn?

Doing this project, our group learned more about compilers and the steps of how to make one from scratch. We found it interesting that we were able collaborate and hear different ideas as to how we should go about creating a compiler and how our different styles of coding blend together to attempt to create a functioning compiler. We found it rather difficult to actually get the compiler to run an executable file. We have managed to get through the step of compiling the file, but when we would go to execute, we were getting an error that our .o file couldn't be found even though the compiler was creating the file. For next time, we would definetly start our project earlier so we can spend more time debugging our code. We feel as though if we had started earlier, we would have been able to find the bug in our code that was causeing our executable file to just go into the abyss. 
