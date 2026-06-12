---
title: "Graphic card driver"
date: 2009-02-09
forum: Multimedia Software
---

### Post by warlog on 2009-02-09
I have a laptop compaq v6608au. I installed ubuntu 8.10 on it. It was working fine. After that I installed graphic card driver.
When I restarted my laptop the login screen comes in proer resolution of 1280x800. But after giving my username and password my TFT screen goes off. Can anybody help me in this issue?
I am having NVIDIA GeForce 7150/nForce 630i graphic driver.

---

### Post by khelben1979 on 2009-02-09
What driver version did you install and how did you do it?

Also, post this file /etc/X11/xorg.conf to this thread so it'll be possible to see how your graphic configuration looks like over there.

---

### Post by warlog on 2009-02-11
I installed the driver provided by nvidia form the following link:
[http://us.download.nvidia.com/XFree86/Linux-x86/180.22/NVIDIA-Linux-x86-180.22-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/180.22/NVIDIA-Linux-x86-180.22-pkg1.run)

Steps used for installation:
1. boot the computer in recovery mode from boot loader.
2. execute the command :
   sudo sh NVIDIA-Linux-x86-180.22-pkg1.run <enter>
3. Follow on screen instructions.
4. All done. Restart the computer.

---

### Post by khelben1979 on 2009-02-11
Did the install went through without errors?

I don't know what's wrong right now. I would like to advice that you post your problem [on this nVidia Linux forum]("http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14") if you haven't already done this to improve your chances to get help on this.

---

