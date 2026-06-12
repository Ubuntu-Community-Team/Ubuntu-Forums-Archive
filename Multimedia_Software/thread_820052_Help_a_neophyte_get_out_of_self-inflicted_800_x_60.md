---
title: "Help a neophyte get out of self-inflicted 800 x 600"
date: 2008-06-05
forum: Multimedia Software
---

### Post by GeneVostok on 2008-06-05
Because i wasn't getting any accelerated desktop effects with my 9600 GT i tried downloading and installing the newest Nvidia Linux drivers.  However, everytime i tried to "sudo" them, they said that the package couldn't be opened.  Subsequent tries in the Terminal said the "sudo" wasn't recognized as a command, so i could only try once between restarts (???).

So, reading up on these boards, there have been several lists of things to try to change.  I was following these instructions below the best i knew how, but most of the commands are foreign to me.

I tried doing what this post following recommended; but i forgot to hit return after entering my password before hitting Ctrl-Alt-F1.  I didn't realize this would kill the GUI and throw me into command line. 

> So this is what I did:
open terminal:
cd /lib/linux-restricted-modules

sudo rm .nvidia*

use Synaptic and remove all nvidia files such as :
linux-restricted-drivers
xserver-xorg-video-nv
nvidia-xconfig
nvidia-settings
nvidia-kernel-common
then:
downloaded the NVIDIA driver - I used 173.14.05
sudo chmod +x NVIDIA-Linux-x86_64-173.14.05-pkg2.run ( note this is for 64 mode)
(note place this in you home directory - easy access)

press Ctrl+Alt+F1
log in 

enter:
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86_64-173.14.05-pkg2.run (say yes to all prompts)
sudo reboot

So i did everything but the last 2 lines.

When i restarted Ubuntu, i only have 800 x 600 as the highest screen option.  So i tried retracing my steps in the Symantic manager and reinstalling all the packages i removed (at least to get back full screen, i thought), but these changes didn't help.  I tried restarting gdm (... /gdm start) and restarted, and .. still stuck in 800 x 600.  

So i followed a new set of instructions, that referrenced the "nano" command, sort of an edlin-y thing, but i don't know how this process works; i suppose i'm trying to either create or modify a text file, but i can't quite figure it out without a lot more research and time spent.

Hopefully, you guys have some ideas, and this is an easy fix for those with experience.... Any assistance is appreciated!

---

