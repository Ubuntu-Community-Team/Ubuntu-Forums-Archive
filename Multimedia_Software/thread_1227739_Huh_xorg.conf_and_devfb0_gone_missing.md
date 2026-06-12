---
title: "Huh? xorg.conf and /dev/fb0 gone missing?"
date: 2009-07-31
forum: Multimedia Software
---

### Post by Ubuntiac on 2009-07-31
I'm running Karmic and had some blocked updates yesterday, so I ran a dist-upgrade and all seemed well... until this morning.

Now when I boot, instead of X I just get a blank screen. Ctrl+Alt+F1 and some investigation showed no xorg.conf file exists (even after dpkg-reconfigure xserver-xorg). When I created this manually nothing changed.

Xorg.0.log sounds like everything's fine, ending with a whole bunch of statements like "unblank CRTC success!" which doesn't sound like its having trouble. The only error is about r600_dri.so not existing and that it's falling back to software rendering - which is apparently normal as this hasn't been released yet.

My xorg.conf is completely default and is set to use the ATI driver.

Anyone have any ideas where to look for a solution to this? I promise I'll mark it "solved" and share when I find a solution! ;)

Thanks in advance!

---

### Post by ZijWePro on 2009-11-01
Kicking this thread because I got almost the exact same problem with a clean Ubuntu 9.10 install...
Troubleshooting asap. would be great, as I installed Ubuntu on my notebook for school and I'm not into re-installing Windows again...

Thank you in advance!

---

### Post by yyyc186 on 2009-12-06
There is a bug filed in launchpad.  I assume you have nvidia video.  It wasn't any of the Xorg updates, but some supporting library update busted NV drivers bad.  The bug has been confirmed.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/492121](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/492121)

I have not received any updates about anyone working on this problem. There are a lot of "confirmed" bugs which aren't assigned to anybody.  It would be nice if someone would simply identify which supporting library busted this so we could back it out until the powers that be had time to fix it.

To anyone else running Nvidia and Karmic/9.10, DO NOT APPLY ANY UPDATES UNTIL THIS BUG IS FIXED.  Once that happens you can only log in as a console user.

---

### Post by sdowney717 on 2009-12-06
so can you download the latest nvidia binary driver
make it executable chmod +x
boot into recovery mode 
run the installer
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

or can you run the one included in synaptic ubuntu packages?

I dont use the nv driver.

---

### Post by yyyc186 on 2009-12-06
> **sdowney717 said:**
> so can you download the latest nvidia binary driver
make it executable chmod +x
boot into recovery mode 
run the installer
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

or can you run the one included in synaptic ubuntu packages?

I dont use the nv driver.
You cannot do anything which requires X graphics.

There is also another bug thread which may or may not be related.  It appears Nvidia is having a rather rough time getting anything usable out the door.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/469470](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/469470)

---

### Post by Ubuntiac on 2009-12-06
Can't remember how I fixed this, but I'm actually on ATI...

---

### Post by domagoj91 on 2009-12-06
> **Ubuntiac said:**
> Can't remember how I fixed this, but I'm actually on ATI...

Hi please can you remeber i have the same problem...

---

### Post by sdowney717 on 2009-12-06
actually you can download the file in the terminal
and
cant you just
sudo apt-get install nvidia-185*?

> scott@scott-desktop:~$ sudo apt-get install nvidia-185*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-180-libvdpau-dev for regex 'nvidia-185*'
Note, selecting nvidia-185-libvdpau-dev for regex 'nvidia-185*'
Note, selecting nvidia-185-libvdpau for regex 'nvidia-185*'
Note, selecting nvidia-185-kernel-source for regex 'nvidia-185*'
Note, selecting nvidia-180-modaliases for regex 'nvidia-185*'
Note, selecting nvidia-185-modaliases for regex 'nvidia-185*'
Note, selecting nvidia-180-kernel-source for regex 'nvidia-185*'
Note, selecting nvidia-180-libvdpau for regex 'nvidia-185*'
The following packages were automatically installed and are no longer required:
  python-psyco
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nvidia-180-kernel-source nvidia-180-libvdpau nvidia-180-libvdpau-dev
  nvidia-180-modaliases nvidia-185-libvdpau nvidia-185-libvdpau-dev
The following NEW packages will be installed:
  nvidia-180-kernel-source nvidia-180-libvdpau nvidia-180-libvdpau-dev
  nvidia-180-modaliases nvidia-185-libvdpau nvidia-185-libvdpau-dev
0 upgraded, 6 newly installed, 0 to remove and 9 not upgraded.
Need to get 75.2kB/90.4kB of archives.
After this operation, 270kB of additional disk space will be used.
Do you want to continue [Y/n]? 


---

### Post by kalmos on 2009-12-06
I'm glad I found this thread, because I'm having a very confusing experience with this problem. I thought my installation of CUDA drivers had caused the problems. According to this thread, it seems that it's not my fault that now I get a black screen after boot.

My experience:
1. Everything worked fine on Ubuntu version ???.14, and I decided to install CUDA drivers from nv to try it out.
2. Installing the drivers worked fine.
3. I installed some updates from the automatic system updater, and then restarted. After restarting, in grub I selected version ???.15.
4. Black screen after the Ubuntu logo disappeared, no terminal or gui. So, I assumed that I made a mistake when I installed the CUDA drivers.
5. Next, I tried to boot into ???.14, but I still got a black screen.

To fix the problem, I used a different Ubuntu on another partition to download the latest driver from nv, something like "NVIDIA-Linux-x86-190.??-pkg1.run". Installing this on the ???.15 version did not help with the black screen, but installing it on the ???.14 version worked and I got my GUI back.

I can't remember the specifics now, but I updated to the next Ubuntu version, ???.16 and I get the black screen on boot again. I'm now using windows until I have time to fiddle with the issue again.

I'm still confused about the cause of the problem and a solution, so any attempt at enlightening me would be greatly appreciated.

---

### Post by sdowney717 on 2009-12-07
you should just use the .14 kernel for now as obviously there is a problem with the .15 kernel and .16 kernel
I noticed the .16 kernel is being held back.

with the new grub version, you dont get a grub menu at boot if your only os is ubuntu. you can change this by editing /etc/default/grub and commenting out this line using a # sign

the devs ought to change this since people upgrade and then cant login with the new kernel upgrades.

#GRUB_HIDDEN_TIMEOUT=0

---

