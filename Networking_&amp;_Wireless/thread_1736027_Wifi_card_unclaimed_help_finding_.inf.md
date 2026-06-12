---
title: "Wifi card unclaimed help finding .inf"
date: 2011-04-22
forum: Networking &amp; Wireless
---

### Post by Brumbinhd on 2011-04-22
I've seen it done on YouTube etc.. My wireless card when I run the command to check it's status comes back as "unclaimed" I get that I need to use that *ndsiunwrapper (*excuse my spelling on that) program and install the .inf file for my windows driver right? At least that's what I understand... Problem is I can't find the .inf file for my wireless card.... I find downloads for the driver etc.. But none come in an extractable .zip file. They are all .exe.. Where in gods name can I get that .inf? And if there is a different way please someone fill me in! I'm new to the whole Linux thing and it's driving me insane trying to figure this out. I have an HP G-62 laptop, dual booting windows 7 home premium and ubuntu 10.10... My wireless card that I need the .inf file for is a "Ralink RT5390 802.11b/g/n WiFi Adapter"...  Thanks everyone

---

### Post by valroadie on 2011-09-21
Second this, I am having the same problem extracting the .inf file from the exe. Was not able to find a suitable download of cabextract or any other program to open the data.cab files. Someone please help us! Thank you.

---

### Post by bkratz on 2011-09-22
You might want to look at this thread.

[http://ubuntuforums.org/showthread.php?t=1743525](http://ubuntuforums.org/showthread.php?t=1743525)

---

### Post by varunendra on 2011-09-22
> **bkratz said:**
> You might want to look at this thread.

[http://ubuntuforums.org/showthread.php?t=1743525](http://ubuntuforums.org/showthread.php?t=1743525)
@Brumbinhd, I would suggest to follow the above ^ suggestion first.

But if you are absolutely desperate about trying ndiswrapper first, you may have to do this (assuming the location of files in win7 is same as in win XP):

[LIST=1]
[*]The inf files (for installed drivers) are stored in **windows\inf** folder, which is a system folder and as such, hidden. You can simply enter **C:\Windows\inf** in the address bar (assuming windows 'sees' itself in C: drive) to get into it. There may be hundreds of files among which you will have to locate the one you need.
[*]If you open the inf file in notepad, you may find some lines about a '.sys' file, and maybe a '.cat' file. The sys file is the actual driver, inf is only its configuration settings. So you will also have to find and copy that sys file from \windows\system32\drivers directory.
[/LIST]
Now with these two files (.inf and .sys, can't say if the .cat file is important) you may proceed with ndiswrapper.

[DISCLAIMER:) : I have never ever used ndiswrapper myself, it's only my assumption that it MUST require both the sys file and the inf file.]

---

### Post by chili555 on 2011-09-22
> it's only my assumption that it MUST require both the sys file and the inf file.Some do and some don't. Typically, if a driver in Linux-land requires firmware, the .sys file is needed. In any case, it's best to have the .inf and .sys in the same directory when you install the .inf file. If it's needed, ndiswrapper will grab the .sys file. My suggestion is to copy the .inf file, any and all .sys and .cat files to a separate folder in your /home/user directory and let ndiswrapper grab any it needs. Be sure you get the XP files and the files appropriate to your system; i.e. 32- or 64-bit.

---

