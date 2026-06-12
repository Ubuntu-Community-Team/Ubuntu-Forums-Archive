---
title: "Nvidia Optimus"
date: 2014-05-11
forum: Multimedia Software
---

### Post by night116 on 2014-05-11
I have a Toshiba Qosmio
Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz
800.000 MHz
memory 32349mb
network controller:
intel dual band wireless AC 7260
ethernet contoller: qualcomm atheros AR8161 gigabit ethernet rev10 

I changed the graphics settings from xorg to the recommended nvidia-331 as it was not showing up the correct resolution, but now when I boot into ubuntu 14.04 I get the log in screen to put my user and code in but then it just goes to the ubuntu picture but never logs or shows the desktop.
I trid to boot into terminal and reinstalling the drivers to no avail.
I have tried
ubuntu-drivers devices | grep recommended
and it shows up as 
driver : nvidia-331 - distro non-free
but I cant get it to work any other way and cant get to a desk top

---

### Post by kc1di on 2014-05-11
Hi night116, 

can you get to a terminal and post the output of the following command?
```
lspci | grep VGA  
```

will try to help.

---

### Post by night116 on 2014-05-11
Yep i can get to a terminal via secure boot, the output was the following
00 : 02.0 vga compatable controller : intel corporation 4th gen core processor integrated graphics controller (rev 06)

---

### Post by night116 on 2014-05-11
I have a gk106m geforce gtx 770m
It states  i am using drivers
Nvidia-331 - distro non - free
Xserver-xorg-video-nouveau- distro free builtin
Nvidia-331-updates - distro non- free

---

### Post by WigginsACK on 2014-05-11
It looks like you have an optimus based set up. When you installed nvidia did you run the nvidia-xconfig command or let nvidia rebuild the xconfig file? 

That broke my optimus install. I went with apt-get install bumblebee bumblebee-nvidia nvidia-337 primes nvidia-337-uvm after a apt-get purge nvidia*

That fixed it

---

### Post by night116 on 2014-05-11
I ran the sudo apt-get purge nvidia*
But get the following
W: not using locking for read only lock file /var/lib/dpkg/lock
E: unable to write to /var/cache/apt/
E:the package list or status file could not be parsed or opened

---

### Post by night116 on 2014-05-11
I set the config of the graphics from within the system settings ubuntu

---

### Post by kc1di on 2014-05-11
> **night116 said:**
> I ran the sudo apt-get purge nvidia*
But get the following
W: not using locking for read only lock file /var/lib/dpkg/lock
E: unable to write to /var/cache/apt/
E:the package list or status file could not be parsed or opened

do the following to clear the lock file.  
make sure you don't have any other package manager running.
if not 
```
sudo rm /var/lib/apt/lists/lock
``` also ```
sudo rm /var/cache/apt/archives/lock
```
then ```
sudo apt-get update
```
try the purge again.

---

### Post by night116 on 2014-05-11
Rm canot remove /var/lib/apt/lists/lock read-only file system

---

### Post by night116 on 2014-05-11
I notice that in the recovery menu the file system states it is only read only, so how to get to a real command prompt that works, i did click on the drop to root shell command

---

### Post by kc1di on 2014-05-11
change the permission then 
```
sudo chmod 775 /var/lib/apt/lists/lock
```

---

### Post by night116 on 2014-05-11
I finally got the locks cleared but the packages you stated above bumblebee 337 are unable to be found

---

### Post by night116 on 2014-05-11
Haha
I used you rm var etc and instructions above but the bumblebee package could not be found, so i just rebooted the system and woohoo it booted up to the desktop.
On the system setting under additional drivers it back to using the x.org x server-nouveau display driver.
But woohoo it works like it did before
Thanks heaps for your help

---

### Post by kc1di on 2014-05-11
glad it working for  you. Enjoy!

Please take a moment and mark the thread Solved. - Thanks

---

