---
title: "Driver for ATi Radeon X1900 GT"
date: 2009-06-13
forum: Multimedia Software
---

### Post by rogueleader12345 on 2009-06-13
I have an interesting problem. I have Intrepid on my 4 gig flash drive. I use it on my computer, which has an ATi Radeon X1900 GT installed in it. When I boot it up, I must use "Safe graphics mode" or else the screen frags. So I figured "Aha! I don't have the ATi driver installed!" So I installed it, and at the completion screen it said something like "If your screen stops working, then enter this line into any open terminal. _thisline_" So I restarted and tried to boot back into it, but I wouldn't even get the boot screen. So I blanked the flash drive and reinstalled Ubuntu. Plus, I couldn't turn on any desktop effects. My question is, can I install the ATi driver, then BEFORE I reboot enter that line into the terminal to fix it? Since I'm running it off of a flash drive, I get the Live CD menu, and so I can't get a terminal. Any ideas folks? Thanks in advance.
-Rogueleader12345-

---

### Post by rogueleader12345 on 2009-06-15
Since I upgraded to Jaunty, it won't even let me into System->Preferences->Display, and the Catalyst Center won't work.

---

### Post by HappyFeet on 2009-06-15
Good luck trying to mimic a real install on a flash drive. It is not the same, and you should not expect the same results. Perhaps a real install on one of those small portable hard drives is a better choice. Just remember to install grub to the external drive or unplug any internal drives before installing.

Flash drive installs are hit or miss at best.

---

### Post by rogueleader12345 on 2009-06-15
I have it running just like an installed version on my flash drive. I just need to know if I can enter that line before I reboot without the screen blanking.

---

### Post by rogueleader12345 on 2009-06-18
Bump

---

### Post by rogueleader12345 on 2009-06-23
Bump. Please, if anyone knows ANYTHING, please post.

---

### Post by masux594 on 2009-06-23
The answer is "Unfortunately, No".. The R5xx legacy [all graphic cards before HD2xxx series], were unsupported from jaunty because the OFFICIAL ati catalyst [from X1xxx and before] doesen't support Xserver 1.6[from jaunty].. If you want some drivers for JAUNTY, you can move to RadeonHD open source drivers [[installation guide]("https://help.ubuntu.com/community/RadeonHD")].. otherwise if you want to use official ati catalyst you must use ubuntu 8.1 or older..

Sysc, A

P.s. I had the same problem with mi x1950pro and with RadeonHD drivers all works fine!

---

### Post by rogueleader12345 on 2009-06-23
Ok, thanks. But when it installs the generic drivers, I reboot and I just get the loading screen. The bar keeps bouncing back and forth, and it doesn't load. Any ideas?

---

### Post by masux594 on 2009-06-23
Maybe searching for something.. Generic drivers? jaunty 32bit? hmm, i think that the generic drivers isn't useful.. Listen to me, try uninstall all the crappy default generic etc drivers.. And just follow the guide of the previous post.. Let me know if you have some problems! 

Sysc, A

P.s. Can u see the desktop? Or it didn't boot at all?

---

### Post by rogueleader12345 on 2009-06-24
When I installed the generics, I didn't even get the desktop. All I got was the loading bar. Oh, another piece of info. When I boot, I have to use "Safe Graphics Mode" or else when it boots (if it does at all, it's hit or miss) the windows lag and freeze the screen. Those drivers look like they're for the Radeon HD series, which my X1900 GT is not a part of. Question, is it possible to tell Ubuntu to just use the onboard Intel Graphics Accelerator? If so I may just do that, because I know that works fine.

---

### Post by masux594 on 2009-06-24
> **masux594 said:**
> 
P.s. I had the SAME problem with mi _***x1950pro***_ and with RadeonHD drivers all works fine!

Sysc, A

P.s. Why use the integrated graphic accelerator when your graphic card is more powerful??

---

### Post by masux594 on 2009-06-24
Quoting from the guide of the link:
>  [..] the radeonhd driver offers accelerated 2D/3D/Xv for R5x0 (X1k cards & 690G IGP) [..]  

Sysc, A

---

### Post by ssri on 2009-06-24
If you upgraded to Jaunty from an Intrepid install that had fglrx (ATI's proprietary driver) working, then you have to boot into the console and then type:

sudo apt-get remove --purge fglrx*
sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa mesa-utils
sudo apt-get install --reinstall xorg xserver-xorg xserver-xorg-core

sudo apt-get install xserver-xorg-video-ati xserver-xorg-video-radeon
-or-
sudo apt-get install xserver-xorg-video-ati xserver-xorg-video-radeonhd

and then...

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by rogueleader12345 on 2009-06-25
I am in the process of reloading my Jaunty on my flash drive, so as soon as I do I'll try it and let you know.

---

### Post by rogueleader12345 on 2009-06-25
It wouldn't install them. I haven't rebooted yet, but I hope it doesn't crash...

---

### Post by rogueleader12345 on 2009-06-26
Well it didn't crash, but I'm back at square one. So let's look at option B. How can I use the Intel Graphics Accelerator that's on my motherboard? I know that works fine in Ubuntu.

---

### Post by rogueleader12345 on 2009-06-29
Does anyone know how to switch back to the Intel graphics instead of my Radeon, without taking the Radeon out or changing which one I use in Windows?

---

### Post by rogueleader12345 on 2009-07-01
Does anybody know how I can use the Intel onboard graphics instead of my Radeon?

---

### Post by alphacrucis2 on 2009-07-01
> **rogueleader12345 said:**
> Does anybody know how I can use the Intel onboard graphics instead of my Radeon?

My guess would be that you would have to do that in the BIOS config on boot up.

---

### Post by masux594 on 2009-07-14
For install the intel graphic aaccelerator there's an [entire thread]("http://ubuntuforums.org/showthread.php?t=1130582") about that..

Sysc, A

---

