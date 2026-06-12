---
title: "Flash/GNASH/litespark - nothing works...."
date: 2012-10-13
forum: Multimedia Software
---

### Post by Kev Black on 2012-10-13
&#65279;I'm trying to rid myself of windows hand have xbuntu running on my old PC, and it's great...
EXCEPT
The main sites my kids use are Friv, and CBBC, which are all loaded with Flash and I can't get it to work.
I've been trying to follow the various threads but getting not very far and I hope to get some help.
I'm new to Linux, but computer literate and actually programmed UNIX system V 20 years ago (but so long it is all forgotten now!)

My machine is and old Evesham PC
 It has an AMD Athlon XP 2700 CPU, 120Gb free drive space, but only 1/2 Gb of RAM.

graphics reported are:
kev@kev-linux:~$ lspci -nnk | grep -iA2 vga
 03:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI R350 AH [Radeon 9800] [1002:4148]
 Subsystem: Advanced Micro Devices [AMD] nee ATI Device [1002:4f72]
 Kernel driver in use: radeon
 
Currently I have installed the ristricted extras package and Firefox reports
Shockwave flash 11.2 r202

Using this when i show a page with embedded flash I see nothing....the "space" where the video would be remains white (the background colour)


When I use flash aid and install GNASH on Firefox an embedded video window still is shown, but not playable, and below the still it reports 
C&#65279;annot play media. You do not have the correct version of the flash player. Download the correct version


If I use lightspark from flashaid firefox addons reports 
Shockwave flash 11.1 r550

When I load a page, the video “nearly starts” - the circlating arrow begins but then it reports
We’re sorry lightspark encountered a yet unsupported Flash file
SWF file: [long url here which I can’t copy]
Cause unhandled ActionScript exception.

I’m really struggling with what do do - without this Flash capability I pretty much am stuffed, so I hope someone can help.

Thanks in advance.

K

---

### Post by uconvert on 2012-10-22
I just went through this problem and posted a fix on another thread

[http://ubuntuforums.org/showthread.php?t=2049888](http://ubuntuforums.org/showthread.php?t=2049888)

Hope this works for you!

---

