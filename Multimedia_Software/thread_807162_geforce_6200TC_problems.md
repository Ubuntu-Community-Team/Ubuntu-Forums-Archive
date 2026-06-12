---
title: "geforce 6200TC problems"
date: 2008-05-25
forum: Multimedia Software
---

### Post by jond2005 on 2008-05-25
Hi all, Im new to the ubuntu world and so far i like it but im having trouble with my video card.



I installed ubuntu 8.04 hardy heron and am using an nvidia geforce 6200TC. Everything runs fine and looks great. I want to install the proprietary drivers so i can take advantage of 3d and try and use that beautiful compiz. I install the proprietary drivers and reboot and then everything goes downhill from there. I log in and my desktop comes up but everything runs extremely slow and certain tabs wont even respond to my mouseclicks. I cant click on certain things and everything is just slow in general. Terminal comes up but i cant even type any commands in it. Its like it doesnt respond. I have uninstalled the propreitary driver for now and just using the basic stock stuff that comes with ubuntu. I hope you guys and gals can help me. thanks.

---

### Post by xc3RnbFO8P on 2008-05-25
Did you enable the nvidia driver in 

System> Administration> Hardware Drivers ?

---

### Post by jond2005 on 2008-05-25
yes i did, and when i turn that driver on and restart is when everything starts running slow and messed up.

---

### Post by jond2005 on 2008-05-26
bump for help, this problem is driving me crazy.

I also tried using the envy drivers and that didnt work.

I also tried install the nvidia drivers from the website in terminal mode but it talks about how i dont have the right libc libraries to compile a kernal or something like that. Ive tried reading and searching but i cant find anything. thanks for the help.

---

### Post by xc3RnbFO8P on 2008-05-26
You can try  envy:
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

Or This:
[http://ubuntuforums.org/showthread.php?p=4978329]("http://ubuntuforums.org/showthread.php?p=4978329")

---

### Post by jond2005 on 2008-05-27
ok ive already tried envy and when i try using those drivers, i reboot and i get a box saying x is running in low graphics mode so that didnt help.

I also tried the second solution and the installer gives me an error message stating:
 "ERROR: You do not appear to have libc header files installed on your system. Please install your distribution's libc development package."

ah man i just wanna get this to work. thanks for your help hopefully we can get this working.

---

### Post by xc3RnbFO8P on 2008-05-27
In Synaptic Package Manager:

Settings> repositories> Ubuntu Software check all, uncheck cdrom

Settings> repositories> Update> check all

Settings> repositories> Third-Party-software> check
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) partner
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) partner (source)
Reload
If you haven't.

---

### Post by xc3RnbFO8P on 2008-05-27
In Synaptic P M, search libc6

install libc6 and **libc6-dev**

---

### Post by jond2005 on 2008-05-27
ok i got all those packages and tried installing the proprietary driver from system<administration hardware drivers and it still didnt work. However when i rebooted everything looked very good and things started working a little faster but i still could not type in the terminal and click on certain tabs. Some things just dont respond.

i then tried what u suggested up above:
Or This:
[http://ubuntuforums.org/showthread.php?p=4978329](http://ubuntuforums.org/showthread.php?p=4978329)

the nvidia installer was able to compile the kernel it needed thanks to those packages u told me to get. The nvidia install worked and the same thing still happens. Everything is slow and i cant type in terminal and certain buttons wont respond. I just dont understand. The picture looks beautiful, i just wish everything would work. I think we are getting closer to a solution though.

---

### Post by jond2005 on 2008-05-27
***OK I GOT it working with the 169.12 drivers but my resolution sucks 5 only get 640 x 480 or lower. I cant have everything that big. Any ideas what to do now?

Actually i take that back. I think it reverted to using some old kind of nvidia drivers cuz my xorg.conf reads:
Section "Device"
  Identifier "Configured Video Device"
  Driver "nvidia"
  VendorName "NVIDIA"
  BoardName  "NVIDIA GeForce 6 Series"


that means its just using some generic nvidia driver and not the driver for my 6200tc right?

---

### Post by jond2005 on 2008-05-30
OK PROBLEM SOLVED!

I went here:
[http://ubuntuforums.org/showpost.php?p=4789536&postcount=110]("http://ubuntuforums.org/showpost.php?p=4789536&postcount=110")

This enabled me to pick out what monitor i was using and then after that i could change my screen resolution. After this everything is working perfect. I have enabled 3d and have compiz running and everything looks awesome. Thanks ringi for helping me trouble shoot

---

