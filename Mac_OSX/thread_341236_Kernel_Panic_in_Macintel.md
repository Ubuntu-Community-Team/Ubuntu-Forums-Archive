---
title: "Kernel Panic in Macintel"
date: 2007-01-18
forum: Mac OSX
---

### Post by Scheater5 on 2007-01-18
Alright, so I may or may not get the best support for this on an Ubuntu forum - but you guys are usually my first stop when I have a problem.  Hey, if it works don't mess with it!

NEway, a couple of you know I botched two harddrive in an attempt to create a macintel (which, I have recently learned, the actual Mac community trys to refer to as "hackintoshes" to diferentiate from "normal" macs with intels).  But, I've still kinda got the itch - call it my white whale.  
So, I established one computer as a "sandbox" and did the same with one external harddrive.  And made amazing advances - OSX is now installed on a (relatively) old Compaq.  But I have a problem.  No sooner does the Darwin loading screen pass than I get a kernel panic.  Booting in safe mode gets me no joy.  I did finally manage to get it to be verbose with the error message, and if that'll help I'll post.  But I'm not entierly sure it will help diagnosing the problem.  The OSX website suggests resetting PRAM as one possible solution - but I can't find how to do that from the Darwin screen - and somehow I fear it related to hardware.  Anyone have any suggestions, solutions or ways to further diagnose?

---

### Post by Alfa989 on 2007-01-18
Doesn't it work if you hold command+option+P+R?

---

### Post by Scheater5 on 2007-01-18
Alright, when I said hackintosh, I meant a normal "PC" with "that VMware image" on it, as per instructions on UneasySilence (trying to avoid any legal hangups I could get myself in).  As such, I have a "normal" keyboard layout.  Do you know what keys would OSX read as command and option??  Remember, I'm getting a Darwin screen first where I put in options, whereas "normal" macs hold down the keys.

---

### Post by 3rdalbum on 2007-01-19
PRAM is indeed related to hardware - in fact, it's a piece of hardware. The Command-Option-P-R code only works before the operating system has loaded on a genuine Macintosh (it's part of the ROM I believe). Sorry I couldn't be of more help, but I'd suggest you find a forum full of people who are in fact running OS X on generic computers, as any information in the Apple knowledge base will assume that you are using a Macintosh computer.

---

### Post by Scheater5 on 2007-01-19
hmmm...alright, so I'll do a bit of research as to what PRAM is, because I don't think I've ever heard of it before this incident.  Thanks.  
And I think I may have found a place with more relevant help - the OSx86 Project.  But I still trust you guys, and if anyone has anything else to add I'll welcome it.  I'm currently in the process of downloading some of the newer install images - "that VMware image" is Tiger, but there are releases up to 10.4.8.

---

### Post by 3rdalbum on 2007-01-20
PRAM = Parameter RAM.

It stores some of the Mac OS's basic control panel settings when the computer is turned off. I think the nearest x86 equivlient is the CMOS.

---

### Post by Scheater5 on 2007-01-22
Thanks for your help - and that's interesting about the relationship between PRAM and CMOS, I never would have made that connection.

---

