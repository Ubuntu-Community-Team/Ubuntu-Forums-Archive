---
title: "help directX"
date: 2009-03-11
forum: Multimedia Software
---

### Post by monkeyslayer56 on 2009-03-11
i can't get any directX games to run through wine COD4 freezes and BFH closes immediately after start and i realy realy want to be able to uninstall my remaining windows instalation also BF2 wouldn't work but that my have ben becouse of directX getting installed but since then i have reinstalled wine and also deleted the/.wine directory please any help at all

---

### Post by thtrgremlin on 2009-03-11
The Call of Duty 4 Wine guide can be found here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=12804](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12804)

---

### Post by monkeyslayer56 on 2009-03-11
no good same problem

---

### Post by Neo_The_User on 2009-03-11
install xchat, connect to freenode, join #winehq

ask

---

### Post by monkeyslayer56 on 2009-03-11
k i'll try to get answers there thanks

---

### Post by thtrgremlin on 2009-03-11
If you run wine from a terminal you can see the error messages / debug output. Post that and might be able to help further.

Also, if you type```
glxinfo | grep render
``` do you get > direct rendering: Yes and what driver does it give in use after that?

That can help track down the issue.

---

### Post by monkeyslayer56 on 2009-03-11
ok i don't think i can do that right now because now i have a MUCH bigger problem i just donwloaded the new NVIDIA driver(i have a geforce 6600gt card) and now i can't start X with out useing the default driver i forget the exact error but i was something like   api kernal missmatch  current 169.x needs to be 180.20
so what do i do now? right now im using the default driver and im guessing no 3d acc since compis isn't working now either and ive been searching google for a solution but can't find one please help me

---

### Post by monkeyslayer56 on 2009-03-11
ok i got the driver installed but no desktop effects and i ran that command and got > [josh@josh-desktop:~$ glxinfo | grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: GeForce 6600 GT/PCI/SSE2
josh@josh-desktop:~$ 


---

### Post by thtrgremlin on 2009-03-11
If you have the right restricted driver installed and you can get to a desktop now, you need to run nvidia-settings as root. If it is not installed:```
sudo apt-get install nvidia-settings
``` after that, just run:```
sudo nvidia-settings
```when you start it up, it will tell you that it has done a backup of xorg.conf and created a new config file. restart the computer and it should work fine. That is what I have had to do for my computer.

Oh, and "direct rendering: No" means that you are not getting any hardware acceleration. After you have done the above including restarting, you can be sure everything is working well if you get to a desktop and run glxinfo | grep render and get "direct rendering: Yes"

---

### Post by monkeyslayer56 on 2009-03-11
k i'll try that but fisrt i got to figure out what happend to my internet on it. it stopped picking up my wirless addapter through all of that im working on a temp bridege from my laptop i'll post the results when i get a chance to try it

---

### Post by monkeyslayer56 on 2009-03-11
it didn't work :( same as before the same message and no effects and it says > You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.  i do that reboot and get the SAME message what can i do this is really getting annoying my hardware is
q6600 quad
geforce 6600gt
1GB ram
ubuntu 8.04 64bit

---

### Post by monkeyslayer56 on 2009-03-12
i got it working i reinstalled ubuntu and wine didn't install anything extra and cod4 started up still downlaoding BFH  though but im happy now there is a good chance it will work and that i will be able to trash my windwos

---

