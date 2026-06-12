---
title: "API Mismatch??"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by Asok on 2007-02-11
Hello, I'm rather new to Ubuntu (and Linux in general), and I've been trying it out for the past few days. I recently attempted to install drivers for my nVidia GeForce FX 5200 card, but when I try to boot into Ubutntu (it's installed on a partition of my hard drive) the loading bar and Ubuntu logo will come up, the bar will fill completely, and then it'll go blank, and stay blank until I restart my computer. I tried starting X from safe mode and this error shows up:

Error: API Mismatch: the NVIDIA kernel module has the version 1.0-8762, but this X module has the version 1.0-8776. Please make sure that the kernel module and all NVIDIA driver components have the same version.

I've tried everything I could find, from using the dpkg-reconfigure xserver-xorg. to installing different(?) drivers (using a guide on these forums), and no luck. Also, whenever I try the reconfiguring, an error pops up after I select the color quality (24 bit, 16 bit, it doesn't make any difference, it still shows up). I've answered question 7 (I can't remember what it was but it said it could be answered no if it didn't work) both ways, with no success. This has been going on for almost a day now, and I'd really love any amount of help I can get. Thanks in advance.

---

### Post by neighborlee on 2007-02-11
> **Asok said:**
> Hello, I'm rather new to Ubuntu (and Linux in general), and I've been trying it out for the past few days. I recently attempted to install drivers for my nVidia GeForce FX 5200 card, but when I try to boot into Ubutntu (it's installed on a partition of my hard drive) the loading bar and Ubuntu logo will come up, the bar will fill completely, and then it'll go blank, and stay blank until I restart my computer. I tried starting X from safe mode and this error shows up:

Error: API Mismatch: the NVIDIA kernel module has the version 1.0-8762, but this X module has the version 1.0-8776. Please make sure that the kernel module and all NVIDIA driver components have the same version.

I've tried everything I could find, from using the dpkg-reconfigure xserver-xorg. to installing different(?) drivers (using a guide on these forums), and no luck. Also, whenever I try the reconfiguring, an error pops up after I select the color quality (24 bit, 16 bit, it doesn't make any difference, it still shows up). I've answered question 7 (I can't remember what it was but it said it could be answered no if it didn't work) both ways, with no success. This has been going on for almost a day now, and I'd really love any amount of help I can get. Thanks in advance.

there were a few hickups  earlier , due to kernel update I believe..

sudo apt-get remove nvidia-glx
sudo apt-get install nvidia-glx

should fix you right up..if not..remove it all and just use 'envy'

found here; 

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

good luck
g.leej

---

### Post by Asok on 2007-02-11
Thanks, neighborlee, I'll try that.

---

### Post by Asok on 2007-02-11
It acts kind of funky when I try to reinstall nvidia-glx. It says: 
> dpkg-preconfigure: cannot connect to X server
debconf: unable to initialize frontend: Kde
debconf: (DISPLAY problem?)
debconf: falling back to frontend Dialog
Selecting previously deselected package nvidia-glx
etc
root@asok-desktop:~# |

So I tried both startx and rebooting into Ubuntu normally, neither of which work, I get the same blank black screen. Also, I'm not quite sure how I can use Envy from the console, so I might need help there, heh.

---

### Post by Asok on 2007-02-12
Is there anything I need to be more specific about? I really need help...

---

### Post by klep on 2007-02-12
I had a similar problem the other day. I had to use envy to fix it. What i did was boot the pc up and when it brought up a blue screen and dumped me into tty i did this:

typed "sudo su -"
types "envy"

chose the option to uninstall nvidia drivers from the options
once that was done chose to reinstall the nvidia drivers.

restarted the pc. That worked for me.

---

### Post by zaopuppy on 2007-07-08
i had a same problem, resolved by compile nvidia kernel self.
apt-get install nvidia-new-kernel-source

then goto /usr/src/module/nv
$ make module
$ make install
$ startx

---

