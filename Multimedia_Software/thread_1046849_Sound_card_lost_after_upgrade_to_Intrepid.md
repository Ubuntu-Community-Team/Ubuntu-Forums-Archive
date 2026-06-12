---
title: "Sound card lost after upgrade to Intrepid"
date: 2009-01-21
forum: Multimedia Software
---

### Post by tv0571 on 2009-01-21
I could use some help.

[LIST=1]
[*] I have an Aureal Vortex 2 sound card in a machine that also has onboard audio via nVidia nForce2 AC97.  lspci-v shows both of them (before and after problems).
[*] I upgraded to Intrepid Ibex from Hardy Heron.  Sound worked before upgrade from the Aureal.
[*] After upgrade, Synaptic flagged nvidia-glx as a package that needed to be purged.  It had problems uninstalling it because of a missing file (I can't recall which).  Until this was fixed, it would not upgrade any other software.   So I touched' the missing file into existence and the uninstall completed successfully.  I was happy.
[*] I rebooted for some reason.
[*] The sound cards were not detected.  They don't show up in System/Prefs/Sound as a device.  aplay -l shows no soundcards.
[*] I followed all the directions in the sticky post about how to fix sound card problems and none of it worked.
[/LIST]

Help is much needed, and appreciated!

---

### Post by markbuntu on 2009-01-22
You can try removing and reinstalling ALSA and see if it automagically finds your cards from a clean state.


(1) Remove the ALSA packages
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```

(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```


Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

``` 

(3) Reboot

---

### Post by tv0571 on 2009-01-23
Thanks for the reply Mark.

I think those same instructions were at the top of one of the sticky posts; but I tried them again anyway.  Doesn't help.  The only thing I noticed as it went through the removal and reinstallation was a message about packages that were installed and no longer required, suggesting autoremove...  here's the return from the last command you suggested (sudo apt-get install gdm etc...):
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtheora-dev libdc1394-22-dev libogg-dev libraw1394-dev libavutil-dev
  libgsm1-dev libvorbis-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fast-user-switch-applet gdm-guest-session
Suggested packages:
  xnest uswsusp gdm-themes
The following NEW packages will be installed:
  fast-user-switch-applet gdm gdm-guest-session ubuntu-desktop
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2463kB of archives.
After this operation, 20.1MB of additional disk space will be used.
Do you want to continue [Y/n]? 
To which I replied y and continued on with no apparent problems.  GDM had never been completely removed but I doubt that is the problem.

I'll be away for a couple of days, but will get back at this when I return.  Thanks.

---

### Post by tv0571 on 2009-01-26
I've tried recompiling the ALSA stuff from scratch by using LordRaiden's instructions on the Comprehensive Sound Solution Guide... I've downloaded the latest drivers (1.0.19) from Alsa and ./configure works OK.  I'm having trouble on the sudo make:
...
> make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.19/misc'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.19/misc'
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.19'
make -C /usr/src/linux-headers-2.6.25-2-386 SUBDIRS=/usr/src/alsa/alsa-driver-1.0.19  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.25-2-386'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.25-2-386'
make: *** [compile] Error 2

I'm not very experienced in compilation, but it seems to get stuck when it looks to the kernel.  Thoughts?

fyi, I've removed my Aureal card to isolate the problem.  I'm only using the onboard Nvidia card now, which, via the Alsa website, I believe to be intel8x0.

---

### Post by Linuxdork on 2009-01-26
Could we see the output on 

```
lspci | grep -i audio
```

---

### Post by tv0571 on 2009-01-26
Sure.  It yields:
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1).

As mentioned, I've pulled the Aureal card until I get at least the onboard working.

---

### Post by Linuxdork on 2009-01-26
Is there anything snd-* in lsmod?

---

### Post by tv0571 on 2009-01-26
no.  i don't see a module or "used by" related to that.

---

### Post by Linuxdork on 2009-01-26
Try

```
sudo updatedb
locate snd-intel8x0 
```

and let me know if it finds anything.

---

### Post by tv0571 on 2009-01-26
Yes, it did.  It returned listings in /lib/modules/2.6.12-10; 2.6.12-9; 2.6.15-23; 2.6.15-25,26,27,28; 2.6.17-12; 2.6.22-16; 2.6.24-21; 2.6-24-22.

And conspicuously absent is 2.6.25-2 which is the kernel i show in uname-r.

hmm....

---

### Post by Linuxdork on 2009-01-26
As long as the output is as follows

```
uname -r
2.6.25-2-generic
```

I think you can try 

```
sudo apt-get install linux-ubuntu-modules-2.6.25-2-generic
```

and then 

```
sudo modprobe snd-intel8x0
```

---

### Post by tv0571 on 2009-01-26
uname -r yields:
2.6.25-2-386

I'm not sure what dictates whether I should be running the -386 kernel or generic.

Thank you for your help.

---

### Post by Linuxdork on 2009-01-27
Okay, try this one:

```
sudo apt-get install linux-ubuntu-modules-2.6.25-2-386
sudo modprobe snd-intel8x0
```

I'm pretty sure that will work.

---

### Post by tv0571 on 2009-01-27
Nothing's easy :)

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-ubuntu-modules-2.6.25-2-386

but it seems like you're on the right track!

---

### Post by Linuxdork on 2009-01-27
I'll bet that's why the module isn't installed.  Are you having problems with any other hardware?  Try it with just:

```
sudo apt-get install linux-ubuntu-modules
```

---

### Post by tv0571 on 2009-01-28
sudo apt-get install linux-ubuntu-modules yields...
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-ubuntu-modules

---

### Post by tv0571 on 2009-01-28
...also, I believe others have had a similar problem (link below), and resorted to the previous kernel.  I'd like to figure out what's wrong with the missing modules so that others don't have to backtrack.  Thanks!
[http://ubuntuforums.org/showthread.php?t=1043175](http://ubuntuforums.org/showthread.php?t=1043175)

---

### Post by tv0571 on 2009-02-02
Does anyone know where or how to get the missing modules I need?  Are these 'modules' specific to the kernel version I'm running?

---

### Post by Ameneon on 2009-02-03
Got the same problem here. This with an old Audiogy 2 card. I'll try reverting back to previous kernel for now.

---

### Post by tv0571 on 2009-02-03
...but the problem must not be limited to the Audigy, because I yanked it and I get the same failures with the sound on the mobo.

---

### Post by Black_Monkey on 2009-02-04
I can't see any packages called linux-ubuntu-modules* - are you sure that's the right package name?
(I don't have any sound either).

---

### Post by tv0571 on 2009-02-04
It would appear that one needs to have linux-ubuntu-modules-<your kernel # here> in order for sound to work.  I have packages for 2.6.24-21-386; 2.6.24-22-386; 2.6.22-15-386; and linux-restricted-modules for many others.  But missing was the 2.6.25-2-386 that matched my kernel.

So I punted and fell back to the previous kernel by editing /boot/grub/menu.lst and commented out the most recent kernel.  It fell back to 2.6.24-22-386.

Now I have sound.  Thanks to Linuxdork for pinning the problem to the kernel version.

---

### Post by SeePU on 2009-02-04
Ubuntu is pretty bad for losing sound.  So many posts about it.  I lost it after an upgrade of the Nvidia driver.  No alsa config utility to use either as I've used it in Debian distros and that always fixes it.  

Way to go Ubuntu!  Way to be like Windows!

---

### Post by madfox8691 on 2009-02-05
thx for that was pulling my hair out trying to fix my sound problem :D

---

### Post by Black_Monkey on 2009-02-05
> **tv0571 said:**
> It would appear that one needs to have linux-ubuntu-modules-<your kernel # here> in order for sound to work.  I have packages for 2.6.24-21-386; 2.6.24-22-386; 2.6.22-15-386; and linux-restricted-modules for many others.  But missing was the 2.6.25-2-386 that matched my kernel.

So I punted and fell back to the previous kernel by editing /boot/grub/menu.lst and commented out the most recent kernel.  It fell back to 2.6.24-22-386.

Now I have sound.  Thanks to Linuxdork for pinning the problem to the kernel version.

Ah, well that sounds like a problem. Any idea why I don't have any packages called linux-ubuntu-modules* in my repos? :(

---

### Post by tv0571 on 2009-02-06
dude - mine's all gone.  But I like Linux anyway.  If you've got the patience to fix the occaisional problem.  Don't think I'll ever build a Windows machine again.

---

### Post by ugm6hr on 2009-02-08
It appears that linux-ubuntu-modules... are no longer packages in Intrepid:
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux-ubuntu-modules](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux-ubuntu-modules)

Those other kernels look like they are Hardy and prior versions.

Not sure where the equivalent drivers are now packaged.

---

