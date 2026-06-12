---
title: "Can Ubuntu emulate OS  X?"
date: 2007-08-08
forum: Mac OSX
---

### Post by ashvala on 2007-08-08
Can you think if Ubuntu can Emulate OS X? (not using virtual emulator like VMware & Wine etc).. I mean that can Ubuntu be OS X?

---

### Post by ErusGuleilmus on 2007-08-08
No, not from what I have been told. The components that make up the OS are to diffrent.

---

### Post by juxtaposed on 2007-08-08
> Can you think if Ubuntu can Emulate OS X? (not using virtual emulator like VMware & Wine etc).. 

Well, if you don't want a compatability later or a virtual machine, there really isn't anything to do...

> I mean that can Ubuntu be OS X?

Ubuntu is Ubuntu. OSX is OSX. Ubuntu is not OSX.

---

### Post by ashvala on 2007-08-08
> > **ErusGuleilmus said:**
> No, not from what I have been told. The components that make up the OS are to diffrent.

Probably it can... MAC OS X is unix.... Leapord works just like linux...
Probably it can

---

### Post by ErusGuleilmus on 2007-08-08
> You can't run OS X apps on Linux because while both are based on Unix, both are quite different. For one, they use different kernels (Linux vs. Mach) , binary formats (ELF vs. Mach-O), and APIs (Carbon/Cocoa vs. X11). Many open source applications used on Linux DO run on both operating systems, since they are ported to run in both environments (MacPorts/Fink are the two well known collections of OSS apps ported to OS X). However, you generally can't run OS X apps in Linux- even virtualization isn't much of an option here, as you can't run OS X reliably in a VM as you can Windows. 

That is a quote from an old post where I asked the very question you are asking now.

---

### Post by slimdog360 on 2007-08-09
supposedly its not too hard to port linux apps over to osx. the other way around though?

---

### Post by 3rdalbum on 2007-08-09
The libraries and services we all like using on Linux have been written to be portable to OS X. Graphical programs use an X server, and OS X does have an X server that you can install. With these open-source libraries, Mac OS X can run some Linux programs.

However, programs written for OS X are built to run with the proprietary Mac OS X libraries on a proprietary graphical layer. Apple has built these things to NOT run on any other operating system.

Finally, I'd like to address another misconception: That Mac OS X cannot be reliably run in a virtual machine. It can, and many PowerPC Linux users do it every day.

---

