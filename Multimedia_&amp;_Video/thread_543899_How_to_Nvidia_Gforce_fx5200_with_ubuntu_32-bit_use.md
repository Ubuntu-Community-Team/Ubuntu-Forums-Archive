---
title: "How to Nvidia Gforce fx5200 with ubuntu 32-bit user(may work with other nvidia cards)"
date: 2007-09-05
forum: Multimedia &amp; Video
---

### Post by nowshining on 2007-09-05
edit - fixed instructions - clearer added used on
 edit - fixed instructions as one optional
 
 
 
 
THIS WAS USED ON FEISTY - Gutsy (it says gutsy in monitoring program and said that it was gutsy testing branch soo I have some feisty in there..) on a Dell 4600i
 
 
 
 **If nothing else works then the instructions in code below may work for u if not Bypass this step.**
 
 
```
 
Open up a terminal
 
type gksudo nautilus
 
filesystem - etc - rc5.d
 
backup and delete nvidia-kernel
 
then go to rcS.d and make sure to backup that one and delete it (i forgot if there is one in there or not)
 
```



Open up a terminal and type gksudo nautilus


go to filesystem - etc - X11
 
 
(yes X11 is an ex and two one's)
 
 
backup and delete xorg.conf
 
 
 
Don't Reboot yet....
 
download 
 
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run)
 
for X86 - 32 bit users
 
now put it where you want it and then close all open windows for now..
 
press the following keys on your keyboard
 
ctrl + alt + f1
 
hit enter after it is done - blinking line
 
enter your username
enter your password
 
sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)
 
 
cd to the folder where the Nvidia .run file is located
 
 sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run
 
 
allow it search for - create and recompile the Nvidia kernel and ACCEPT ALL and OKAY ALL in otherwords follow the instructions with an accept or okay  - to select an answer use the arrow keys left and right then when higlighted in red press the enter key...
 
Also let it create xorg.conf press accept or okay when asked to..
 
sudo /etc/init.d/gdm start (or "kdm start" if you use KDE)
 
now log in and your screen should be in a low resolution - just go into the resolution control panel and select your resolution and or desired Hertz AND if need be select another and then reselect the old one...
 
thanks to this OLD thread in August 2005 for their help.. :guitar:
 
[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)
 
oh and the name of the .run file MUST BE EXACT so the first word is all capitalized again IT MUST BE EXACT...

---

### Post by wolfen69 on 2007-09-05
uh, OK.

---

