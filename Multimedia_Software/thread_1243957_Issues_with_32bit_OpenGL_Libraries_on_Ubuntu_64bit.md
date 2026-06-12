---
title: "Issues with 32bit OpenGL Libraries on Ubuntu 64bit"
date: 2009-08-18
forum: Multimedia Software
---

### Post by beastrace91 on 2009-08-18
My Wine/Cedega applications will not load because of an issue with my 32bit OpenGL libraries... I currently am running the nVidia 190.18 beta drivers (how ever just to be sure it wasn't a driver issue I tried installing the 185.18.31 and they yield the same results) Any idea what I can do to get this working? I have the ia32-libs packaged installed as suggested by many different places online with no luck. I am open to suggestions here - really miss my games :/

Also I can confirm the gfx drivers are installed and working via native 3D apps working correctly.
~Jeff

---

### Post by Natanael on 2011-12-13
For those, who will get here searching for the solution of this problem, as I did.
The only good solution I've found is to add to file association a variable set.

Step by step:
System Settings -> File associations, in the searchbox type exe, click on the arrow on left of application, click on x-ms-dos-executable, in right panel on Wine Windows Program Loader click Change, -> Program, in Command box add at the begining: "LD_LIBRARY_PATH=/usr/lib32/nvidia-current ".

If you want to run other program then exe (like .ahk) must do the same for it's extension.

If you want to run a program not by doubleclicking, but for example from terminal, you must do it like this:
in the program directory, let it be World of Warcraft directory run
LD_LIBRARY_PATH=/usr/lib32/nvidia-current wine wow.exe

and it should run with opengl without problems.

---

