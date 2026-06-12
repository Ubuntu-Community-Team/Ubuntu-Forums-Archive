---
title: "Wrong nvidia module loaded"
date: 2007-02-14
forum: Multimedia &amp; Video
---

### Post by Arnn on 2007-02-14
Hello,

I have a Nvidia  GeForce 8800 GTS card and after installing Ubuntu (6.10 edgy, kernel 2.6.17-11-generic) I downloaded and installed the 1.0-9746 driver from Nvidia manually. After tweaking X configuration some I got everything working. 

First reboot I did gdm didn't start. Looking at the error I concluded that the nvidia kernel module hadn't been loaded. After a "modprobe nvidia" gdm started. I modified the /etc/modules to load the nivida kernel module when booting.

Next reboot gdm still won't start, it now complains about wrong version of the nvidia kernel module. A lsmod reveals that there is a nvidia module loaded. If I do a "rmmod nvidia && modprobe nvidia && /etc/init.d/gdm restart" gdm will start.

This is a bit strange I think. Looks like I have two different nvidia kernel modules on my system and when I boot the wrong one gets loaded but a "modprobe" loads the right one. 

Any suggestions on how to solve this problem?

---

### Post by eyelessfade on 2007-02-14
Indeed, you must remove all trace of nvidia from ubuntu. restricted-modules, nvidia-glx, and maybe also put "blacklist nv" in /etc/modprobe.d/blacklist, then you can do a new:

#sh NVIDIA-Linux-x86-1.0-9746-pkg1.run* -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r


Hope it works :)

---

### Post by morphet on 2007-02-14
Eyelessfade:

you are an awesome ubuntuist. I followed your advice and it still didn't work, but instead of spitting out the long "9746...." drivel it just said "no nv". So I ran the Nvidia .run by itself again, let it do its thing to xorg.conf, and now it works beautifully. thanks :popcorn:

---

### Post by eyelessfade on 2007-02-14
Nice to hear :)

---

### Post by Arnn on 2007-02-15
> **eyelessfade said:**
> Indeed, you must remove all trace of nvidia from ubuntu. restricted-modules, nvidia-glx, and maybe also put "blacklist nv" in /etc/modprobe.d/blacklist, then you can do a new:

#sh NVIDIA-Linux-x86-1.0-9746-pkg1.run* -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r


Hope it works :)

Been a bit lazy since I could get X to run with just a few commands but finally got annoyed enough to try fix it :)

Indeed you are right, I had to remove all trace of nvidia from ubuntu.

Removed following packages:

nvidia-glx
nvidia-glx-dev
nvidia-kernel-common

Then I reinstalled the driver downloaded from NVIDIA but I didn't prefix the lib path as you suggested (wouldn't work). Instead I let the script guess the path. Also I removed my added nvidia entry in /etc/modules cause I noticed it is not needed.

Thanks for the help!

---

