---
title: "Do not support 1920x1200 in DVI mode"
date: 2011-10-16
forum: Multimedia Software
---

### Post by tsingyuan on 2011-10-16
It took me a long time to install Ubuntu on my desktop. And they are all about the Video Support. Let me start it from the very beginning.

I tried to install Ubuntu 11.10 on my desktop. The video card is PNY Geforce 8600GT with two DVI interfaces, and the monitor is SOYO with one VGA interface, one DVI interface and the max resolution 1920x1200. 

I installed Ubuntu through USB drive. However, the installation froze in the boot after several text lines talking about the memory. The graphic interfaces did not event start. It took me a long while to figure out how to solve it. I finally happened to use my roommate's monitor, an HP monitor with max resolution 1600x900. And the installation got through! 

When I finished the installation, I switched back to my monitor and start. The system went to black after the Ubuntu is started.

I then switched back to HP monitor, successfully started Ubuntu, and installed the restricted Nvidia driver(current version). And then restarted the machine. The HP monitor worked very well, and the system automatically chose 1600x900 resolution for the HP monitor. 

I then switched back to my SOYO monitor. This time the Ubuntu started, and the monitor did display. But the resolution was 600x480. I used nvidia-settings to change the resolution. But the 600x480 was already the highest resolution it had. I googled this resolution problem, and tried many methods including changing xorg.conf file. And none of them worked. 

I used the DVI interface all the time till this time. One thing I need to figure out that the DVI interface in the video card and the monitor are both good. This is because I also installed windows 7 on the desktop, and windows 7 worked well with the video card and the monitor in DVI mode.

After that, I happened to have another idea. I used a DVI2VGA adapter at the video card side (there is no VGA interface in the card), and connected the VGA interface in the SOYO monitor. Strange things happened. Ubuntu started successfully and automatically selected the correct resolution 1920x1200 for me. I restarted the nvidia-settings, there were more resolution choices (up to 1920x1200) than the time I used DVI interface.

So finally, I adapted the DVI into the VGA interface to run Ubuntu correctly.

Did anyone meet the same situation before? I will be very grateful if you could provide me some ideas on how to solve this problem,   

Thank you for your patience.

---

### Post by IMvVIP on 2011-12-06
I have been research my problem in google for few weeks and i end here.
First Thank you so much for the detail ex plane problems of DVI connector.
I think i am in same page.
Because my cable it self is DVI - AVI cable which i purchase from BestBuy.
I have been try all linux out there, Fedora 16, Opensuse 12.1 ( it fail install from begining), Linux Mint, Ubuntu ( Wubi ?) 
I have been try out all command out there xorg.conf and even install gnome-tweak ...
all fail me.
every solution was failed.
But after i read this Forum.
I will purchase avi - avi ( i have dvi connector) and let see how it goes.
Linux has been upgrade and upgrade for many years still doesn't support DVI it self....
However thank you for share your exp. and i personally give you big thank you.
I will go head and try this cable problem.
Thank you
Andy

---

