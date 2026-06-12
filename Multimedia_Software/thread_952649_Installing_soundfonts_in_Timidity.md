---
title: "Installing soundfonts in Timidity"
date: 2008-10-19
forum: Multimedia Software
---

### Post by demios on 2008-10-19
I need to run Sibelius 4 through wine. It opens, it runs reasonably well (a slight problem with dialogue boxes not displaying content), and it used to play sound until I tried to install a different soundfont.

The default soundfont was terrible for violins, especially because I was writing fast music, so I tried to install a new one -- [PersonalCopy]("http://www.personalcopy.com/home.htm") -- using [sfarkxtc]("http://melodymachine.com/sfark.htm").

in the right directory with both the files (sfarkxtc and the PC51.sf2, the soundfont) I run

```
./sfarkxtc PC51.sf2
```

which returns

```
======================================================================
sfArkXTc 1.03 (using sfArkLib version: 224)
copyright (c) 1998-2004 melodymachine.com, free for non-commercial use
======================================================================
Uncompressing PC51.sf2...
*** OS ERROR -1 - Failed to open: PC51.sf2

Time taken 0.00 seconds
Result:	File i/o failed
---FAILED--- (errorcode 9)
```


...sigh. long story short, if anyone could point me to a better way of installing soundfonts or configuring timidity (especially to work well with wine), that would be very much appreciated.

---

### Post by kukuntu on 2009-03-16
I had the same problem,
I am new in Linux, and I was installing timidity to run with MMA.
I solved the problem when using "sudo" at the beginning of the command line before ./sfarkxtc... It might seem obvious but I lost 30 min. googling and nothing appeared.

Maybe is too late for Demios but some other people might have the same problem. This way the uncompressor doesn´t give  the errorcode 9, and doesthe job.

---

