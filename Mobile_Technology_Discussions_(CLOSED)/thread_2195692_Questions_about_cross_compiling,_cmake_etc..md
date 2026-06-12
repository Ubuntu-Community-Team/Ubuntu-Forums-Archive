---
title: "Questions about cross compiling, cmake etc."
date: 2013-12-25
forum: Mobile Technology Discussions (CLOSED)
---

### Post by ruwan2 on 2013-12-25
Hi,
I am trying to compiling ARM NE10 library according to: [http://community.arm.com/groups/android-community/blog/2013/09/26/ne10-library-getting-started](http://community.arm.com/groups/android-community/blog/2013/09/26/ne10-library-getting-started).
It uses cmake to configure, then make builds the bin code.
Unfortunately, the process does not look easy yet. The make has errors:

[COLOR=#003366]robert@robert-M5100:~/projectNe10-Ne10-4167142/build$ make[/COLOR]
[COLOR=#003366][  1%] Building C object modules/CMakeFiles/NE10.dir/math/NE10_abs.c.o[/COLOR]
[COLOR=#003366]cc1: error: unrecognized command line option ‘-mthumb-interwork’[/COLOR]
[COLOR=#003366]cc1: error: unrecognized command line option ‘-mthumb’[/COLOR]
[COLOR=#003366]cc1: error: unrecognized command line option ‘-mfpu=vfp3’[/COLOR]
[COLOR=#003366]/home/robert/projectNe10-Ne10-4167142/modules/math/NE10_abs.c:1:0: error: bad value (armv7-a) for -march= switch[/COLOR]
[COLOR=#003366]make[2]: *** [modules/CMakeFiles/NE10.dir/math/NE10_abs.c.o] Error 1[/COLOR]
[COLOR=#003366]make[1]: *** [modules/CMakeFiles/NE10.dir/all] Error 2[/COLOR]
[COLOR=#003366]make: *** [all] Error 2


[/COLOR]


After some testing, I suspect the installed cross gcc is wrong because it has the same message with gcc:
[COLOR=#003366]robert@robert-M5100:~/projectNe10-Ne10-4167142$ arm-linux-gnueabi-gcc --version[/COLOR]
[COLOR=#003366]arm-linux-gnueabi-gcc (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3[/COLOR]
[COLOR=#003366]Copyright (C) 2011 Free Software Foundation, Inc.[/COLOR]
[COLOR=#003366]This is free software; see the source for copying conditions.  There is NO[/COLOR]
[COLOR=#003366]warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.[/COLOR]
 
[COLOR=#003366]robert@robert-M5100:~/projectNe10-Ne10-4167142$ gcc --version[/COLOR]
[COLOR=#003366]gcc (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3[/COLOR]
[COLOR=#003366]Copyright (C) 2011 Free Software Foundation, Inc.[/COLOR]
[COLOR=#003366]This is free software; see the source for copying conditions.  There is NO[/COLOR]
[COLOR=#003366]warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.[/COLOR]



I have several questions. First, If my suspect is correct, I do not know how to remove the wrong  arm-linux-gnueabi-gcc. Then, where and how to install the correct  arm-linux-gnueabi-gcc?

Second, how can I know the more detailed information with the installed gcc. I don't know whether Ubuntu has a tool responsible for managing package, library, utility like OPENSUSE has.

Does any have experience building NE10 library in Ubuntu?
Thanks,

---

