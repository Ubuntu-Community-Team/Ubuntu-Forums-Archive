---
title: "Ridiculously slow 3D performance"
date: 2005-10-26
forum: Multimedia &amp; Video
---

### Post by LoneIgadzra on 2005-10-26
It has recently come to my attention that the peformance of 3D graphics under Linux on my system is abysmal (tried to play Tux Racer). I see that this is a common problem, but as yet I have been stalled in my attempts troubleshoot it based on preexisting topics because apparently something is not right with fglrx.

My Ubuntu installation was originally 5.0.4, and I recently upgraded to 5.10 (not a clean Breezy installation, though the upgrade process seemed to work like a charm following all the instructions to the letter).

So I have done the following:

> sudo apt-get install fglrx-control
sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg
sudo fglrxconfig
[reboot]

The trouble is, after doing all that my 3D provider (sudo fglrxinfo) remains Mesa OpenGL 1.3/1.5, which I am led to believe is undesireable. And the speed problem remains un-resolved. I have uninstalled (doing all the above in reverse) and reinstalled fglrx like ten times.

Also, fglrx seems quite annoying since it causes the resolution preference pane to no longer work so I have to disable all the ridiculously high resolutions my 17" CRT supports while reconfiguring xserver so that I don't get stuck in 1600x1200 or some stupid thing for all eternity.

Everything is fine when I go back to the default ATI drivers, but the speed problem remains.

Before I forget, here are my specs:

AMD Athlon XP 2500+
Radeon 9800 Pro (Sapphire-manufactured)
1 GB RAM
... and so on. I can look up more obscure things like my (ASUS) motherboard's model number, but I sincerely doubt that any of this is necessary. My main point is I'm not trying to use a Voodoo 1 or something.

Thanks!

---

### Post by mlomker on 2005-10-26
Your last two steps were redundant, but the process should have worked.  Look in your /var/log/Xorg.0.log after a failed boot for errors.

Also do a **dmesg | grep fglrx** to look for errors.

---

### Post by LoneIgadzra on 2005-10-26
Here is the output of **dmesg | grep fglrx** following a (yet another) clean reinstall of fglrx:

> william@resnet-5152:~$ dmesg | grep fglrx
[4294717.167000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies , Starnberg, GERMANY' taints kernel.
[4294717.173000] [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
[4294717.173000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294717.191000] [fglrx:firegl_unlock] *ERROR* Process 7957 using kernel context  0

I have no idea what that means of course. (I didn't check the other thing on account of I'm not having any problems with it not booting. I also forgot and - alas - I don't have time at present to boot back into Linux.)

---

### Post by LoneIgadzra on 2005-10-27
Well, I did a clean format & install of Kubuntu 5.10, and - in addition to finding that I like KDE much better than gnome - I was able to get fglrx to install properly, and configure refresh rates and resolutions the way I want them. OpenGL seems to work just fine now. (Unlike gnome's resolution preference pane, KDE's display panel did not get broken by fglrx.)

---

### Post by mlomker on 2005-10-27
I'm glad that it is working!  A lot of people are getting that kernel context error right now...interesting that a reload solved it for you.

---

