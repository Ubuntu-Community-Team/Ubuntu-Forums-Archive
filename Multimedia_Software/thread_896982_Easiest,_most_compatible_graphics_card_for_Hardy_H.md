---
title: "Easiest, most compatible graphics card for Hardy Heron"
date: 2008-08-21
forum: Multimedia Software
---

### Post by Insomniakk on 2008-08-21
Hi,

Just joined and need recommendations for the most compatible and easiest to install graphics card.

Details you prob need to know:
Intel Core 2 6400@ 2.13GHz
Ubuntu 8.04 Hardy
Gnome 2.22.3

I've got a Samsung SM 2232bw and could really do with more than onboard graphics to get the best out of it. 
Nothing too fancy needed though, I'm past my gaming phase!

---

### Post by mrsteveman1 on 2008-08-21
Intels drivers are open source and fully supported but Intel doesn't sell external cards.

Nvidia and ATI seem to go back and forth as to who is more supported or better to use in Linux. ATI seems to be more supportive right now.

---

### Post by collinp on 2008-08-21
If your motherboard has a PCI Express x16 slot, i would go with a Geforce 8600GT. It is probably the best bang for the buck card you can get for under $100 in most cases. And, i believe, the Restricted Drivers will take care of your drivers need without having to download and install the nvidia drivers.

---

### Post by Insomniakk on 2008-08-25
Thanks to both of you for the info.

I've been reading reviews on that 8600 GT and by all accounts it's a whopping great card!
So it's ordered and I should get it sometime this week.
:)

---

### Post by shane19174 on 2008-08-25
Hi,

I bought an 8600 GT about a month ago, and it works great. I was having big problems with an onboard ATI card prior to that. I'm using the newest driver from the NVIDIA website (right now that's version 173.14.12), but I also think (as Hellow suggested above) that the restricted drivers should be fine. Just keep in mind that, if you decide to go for the newer drivers, you'll have to reinstall them with each new kernel version. Either way, hope the card works out for you as well as it has for me.

Shane

---

### Post by Takmadeus on 2008-08-25
Well. right now I am using a Nvidia Geforce 6800 XT and I must say it works even better than with windows. 

Nvidia cards, even with non free drivers are the best you can get these days, had the experience with an Ati card and I must say ati sucks in linux

---

### Post by Usufruct on 2008-08-25
The 9800 GTs can be had for around $130 now, and I've seen the 9600GT for less than $100 (with rebate).  These work in linux, no?

---

### Post by executedisaster on 2008-08-25
> **Usufruct said:**
> The 9800 GTs can be had for around $130 now, and I've seen the 9600GT for less than $100 (with rebate).  These work in linux, no?

Actually the 9 series have a problem with being immediately useable in Ubuntu, likely due to the packaged restricted drivers. I had to jump through a few hoops to get one of my two video cards working, but it works splendidly right now with the most recent beta drivers.

If you get the 9 series, read up on how to get them to work first, and then decide whether it is worth it to you.... also the main difference between the nvidia 8 and 9 series are power usage, not features.

---

### Post by spoons on 2008-08-25
The 9800GT is a rebadged 8800GT and is identical in performance.

---

### Post by richardhickling on 2008-08-27
I have an 9800GT.  Is it truly a rebadged 8800GT?  If it is, clearly I should be able to henceforth treat it as one and search on 8800GT to work out how to get it going.  Right?

I have 2 ViewSonic VX1926wm monitors which I'll get going together once I have everything working with just one.

I'm on 2.6.24-21-generic #1 SMP x86_64

I've tried Envy - but it doesn't recognize my card.

I've downloaded xorgedit - but don't really know how to use it.  I'm going through man xorg.conf but don't have the background info to properly understand it.

Currently I just have 800x600 resolution.  I've tried various changes but I think I just don't have a properly configured driver and have not got the xorg.conf right.  Anyone got a ViewSonic VX1926wm and/or 9800GT or 8800GT working together or separately and can give some info?

I'll keep searching in the meantime.

---

### Post by tuxxy on 2008-08-27
nvidia card definitely, 8600 8800 models are great cards and a good price now, both should run flawless effects and 3D graphics out of the box :)

---

### Post by richardhickling on 2008-08-29
Okay I got my NVIDIA 9800GT working with the 2 ViewSonic VX1962wm monitors ... almost.

To get the NVIDIA drivers going I went here: [http://www.nvidia.com/object/linux_display_amd64_1.0-6111.html](http://www.nvidia.com/object/linux_display_amd64_1.0-6111.html) (since I've got the 64 bit Ubuntu Hardy to best utilize my quad-core and - once I've worked out how to configure it - use all 4G RAM).
 
Steps:
1) Download the installer (NVIDIA-Linux-x86_64-173.14.12-pkg2.run) from above
2) Connect just one monitor then reboot
3) Ctrl-Alt-F1 to go to a text terminal 
4) Find the 'gdm' process using 'ps -aux|grep gdm' or similar and 'kill <process id>' to kill the X-server
5) 'sudo sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run' and choose all the obvious answers including creating a new xorg.conf
6) 'sudo reboot'.  The display should now have full 1680x1050 resolution
7) 'sudo apt-get install nvidia-settings'
8) Connect the second monitor
9) 'sudo nvidia-settings'.  Under 'X Server Display Configuration' you should see a second monitor.  Click 'Configure' and choose 'TwinView'.  Save the changed xorg.conf and Ctrl-Alt-Backspace to restart the X-server

Now I have both monitors BUT ... there are flickering horizontal lines on the second one and it periodically goes black.

Any ideas?

Edit: the problem was caused by a faulty card - I replaced it and now everything is fine.

---

### Post by richardhickling on 2008-08-29
Some more info in case anyone's listening (NVIDIA 9800GT working with the 2 ViewSonic VX1962wm monitors problem):
- The flickering lines are vertical as well as horizontal
- The lines are blue
- The problem is visible even as the BIOS starts up - so it's not Linux specific
- It's not monitor specific.
- It only occurs when both monitors are connected
- It is possible to stimulate the monitor going black by moving a window (say a Firefox browser window) from the working monitor over to the flickering one.

---

### Post by richardhickling on 2008-08-30
This problem is now solved: the card was faulty.  I went back to the vendor who replaced it - everything now works fine.

---

