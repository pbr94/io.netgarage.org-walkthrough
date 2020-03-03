Before going to the level 01, you should visit to their site which is
[[http://io.netgarage.org]{.underline}](http://io.netgarage.org/) . In
this site they mention everything about the event as well as how to
login into the level 01.

![](media/image1.png){width="3.4166666666666665in"
height="0.3854166666666667in"}

You can use either Linux OS or else Windows OS. I am going to use Linux
OS (Xubuntu) because it is really easy. By using "ssh" we can login into
this level. Windows users can use "Putty.exe"
\[[[https://www.putty.org/]{.underline}](https://www.putty.org/) - If
you haven't you can download it from here.\] which is "ssh client" for
the Windows.

Putty guide :
\[[[https://www.ssh.com/ssh/putty/windows]{.underline}](https://www.ssh.com/ssh/putty/windows)
\]

![](media/image2.png){width="4.8590277777777775in" height="5.05in"}After
login into the level they will have give again brief idea about the
level and also about the CTF.

![](media/image3.png){width="6.90625in"
height="1.2972222222222223in"}You should read each and every
instructions are given. This CTF is created on the Linux environment.
Then we can try some Linux commands on here as well because creator can
be restricted some special kind of commands. First of all we should
check file list which are on the current directory. By using "ls"
command we can check them.

![](media/image4.png){width="6.114583333333333in" height="0.9375in"}Here
is the files which are on the current directory. There are few "README"
files with few different languages. You should read one of them because
there are some special instructions about the level.

In the README file they have given these "Game specifics" and they
mentioned all the levels are in the directory "/levels". We should go
into the mentioned directory.

![](media/image5.png){width="3.6847222222222222in"
height="3.0319444444444446in"}

These are the files which are regarding to every and each levels. In
above picture you can see set of files which are related to the levels.
Most of the files are executable and you can see "owners" as well as
"groups" of the files. Then to access those file you have reach each and
every levels.

![](media/image6.png){width="3.0625in" height="0.3229166666666667in"}We
are on level01 and let's try to access that "level01" file. That file is
executable one.

After executing that it asked three digit pass code to unlock that
relevant step. Then we should find that key or a pass code. Let's try
different way to find out that pass code. This level01 file could be
generated from the "C file". Then their should be a "main()" function.
To find that function, we can use reverse engineering mechanism. This is
the best part of this level. Let's see how is going on.

First of all we should disassemble the code which is written on that
level01 file. Because if we open that file with notepad or something
else we can see some byte code which human can't read on it. So we have
to have used "gdb" tool
\[[[https://www.gnu.org/software/gdb/]{.underline}](https://www.gnu.org/software/gdb/)
\] for disassemble that code.

Gdb guide :
\[[[https://www.geeksforgeeks.org/gdb-step-by-step-introduction/]{.underline}](https://www.geeksforgeeks.org/gdb-step-by-step-introduction/)
\]

![](media/image7.png){width="6.916666666666667in"
height="3.1979166666666665in"}

![](media/image8.png){width="6.925in" height="1.738888888888889in"}After
going in to the gdb console, we should find what are functions in this
particular file. To find that follow the instructions which are given
below with the screenshot.

Then we can see the main() function with the temporary breakpoint. We
also can add breakpoints to the code.

Gdb breakpoint guide:
\[[[https://ftp.gnu.org/old-gnu/Manuals/gdb/html\_node/gdb\_27.html]{.underline}](https://ftp.gnu.org/old-gnu/Manuals/gdb/html_node/gdb_27.html)
\]

Now we can disassemble the main() function.

![](media/image9.png){width="3.2395833333333335in"
height="1.7291666666666667in"}

So if you can't understand this format, we can change this format into
another format which is related to Intel.

![](media/image10.png){width="3.0104166666666665in"
height="1.9166666666666667in"}

Above picture will guide you to change disassembly-flavor, current to
another one. In here there are few technical words which are created
using assemble language.

Assembly syntax guide:
\[[[https://www.cs.virginia.edu/\~evans/cs216/guides/x86.html]{.underline}](https://www.cs.virginia.edu/~evans/cs216/guides/x86.html)
\]

I am not going to guide those every syntax, and I have given you a link
which is fully guided about the relevant area. Please go through them.

This code segment should be passing that three digit pass code. Then
there should be a method to compare "pass code" and "your input". In
assembly language we are using "cmp" to compare two parameters. In this
main function in line 4 there is "cmp" function.

0x0804808f \<+15\>: cmp \$0x10f,%eax

or

0x0804808f \<+15\>: cmp eax,0x10f

In those lines (same line with two disassemble-flavors) said, compare
"value which is on 0x10f memory address" and "which we are inputted
value". Then we can print and see that alue which is on 0x10f memory
address. That value could be the pass code.

![](media/image11.png){width="1.28125in" height="0.2708333333333333in"}

Let's try this code as that level01 pass code.

![](media/image12.png){width="5.84375in" height="0.6354166666666666in"}

Great! You got the pass code, and they said that level2 password is
stored inside "/home/level2/.pass" file. Then you can access that file
and find next level password.

![](media/image13.png){width="2.34375in" height="0.2916666666666667in"}

Congratulations!!! Now you have level02 password. And thank you all see
you on next time with level02 walkthrough.
