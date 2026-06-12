---
title: "NVidia Problems"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by justtech on 2007-06-29
It will not let me get anywhere but the "command prompt". Even if I try recovery. But the error that I am getting is

(EE) NVIDIA(0): Failed to Load the NVIDIA kernal module!
(EE) NVIDIA(0): ***ABORTING***

After reading another thread I have found out that it's because I was using a different version of the drivers then I was supposed to due to trying to get Dual Monitors set up. So now how do I get the right drivers from the "Command Prompt"

Thanks for your help

---

### Post by imluxwhoru on 2007-06-29
Ok. I'm assuming that you either used envy to install the driver, or you just upgraded from Edgy to Feisty. Either way the process is the same. First, from the terminal (Or as you call it, the 'Command Prompt';))
```
sudo pico /etc/X11/xorg.conf
```

Then scroll down to -- Section "Device"
Change:
```
Driver "nvidia"
```
to:
```
Driver "nv"
```
Then 'Ctrl + X' to exit pico. It will prompt if you would like to save. 'Y' to say yes, then 'Enter' to save it as xorg.conf

Now, all of that was assuming that your xorg.conf was configured for a 1 screen display. If you already added all the dual screen information, use '#' in front of all the secondary 'Device', 'Monitor', and 'Screen' sections to comment them out (thus telling X to activate only one display) Oh, and also comment out the secondary 'Screen' line under the 'Server Layout' section. Then save and exit pico (see above).

Are we having fun yet?

The next step is to start up X so you can use the computer in a more 'normal' fashion. :) Do this by typing :
```
sudo startx
```
After a second or two of loading, you should be back in GUI business! Now we just have to get the nVidia driver installed proper. I think we should just do it the easy way, and re-install it over itself. So, get Firefox running, and go to [www.nvidia.com](www.nvidia.com). Click 'Download Drivers'. Next, click 'Graphics Drivers' Then, whatever series your card is, then 'Linux x86' (I'm assuming you're running a standard x86 processor and OS, and not a 64 bit processor and OS. If you are, just chose x64). Then click 'Go'.

Next, click 'Download' - NVIDIA-Linux-x86-100.14.11-pkg1.run Make sure and save it to your desktop. While you're waiting for it to download, click on the README toward the bottom of the page and (at least) read chapter 4 and 5 (installing the nVidia driver and yadda.....). You should print those chapters off so you have them while you do the install (you won't be able to use X while installing)

Ok. So, 'Ctrl + Alt + F1' to get into terminal. Then:
```
sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run
```
It will take a bit to install, and you'll have to answer several questions along the way. Just follow the instructions on the README you printed off, and use your common sense.

Once it's all installed:
```
sudo pico /etc/X11/xorg.conf
```
And undo all the changes we made at the beginning (I'm a stinker ehh? :))
```
Driver "nv"
```
Gets changed to:
```
Driver "nvidia"
```
Save and exit pico

If you commented out any dual monitor stuff, I would leave it alone until you know the new driver works. Then, you can go and un-comment it. It's just easier that way.

Reboot (Yes, you really have to reboot). 

That should be it. I'll keep my fingers crossed for ya. Let me know if you have any other Graphic problems. :)

Good luck!!

---

