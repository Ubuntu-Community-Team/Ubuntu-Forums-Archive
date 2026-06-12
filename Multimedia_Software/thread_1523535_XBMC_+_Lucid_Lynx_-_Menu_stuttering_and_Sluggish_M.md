---
title: "XBMC + Lucid Lynx - Menu stuttering and Sluggish Mouse"
date: 2010-07-03
forum: Multimedia Software
---

### Post by Rnegade on 2010-07-03
Hey All,

Well I am a pretty new one with Ubuntu so please be patient. After using 9.4 with XBMC a while ago with no problems I thought I would put 10.4 onto my spare rig for media duties for the kids etc. I got 10.4 installed fairly easily (once I got my HDD issue sorted) thanks to the forums here and I am typing this up on the same machine now. its all running smoothly and responsive except...

... for XBMC. I got it to install (with drama I think) but when I open it up the mouse is like 2 seconds behind the input, its really laggy and stuttery and the keyboard commands are also way behind.

I have opened up System Monitor and then re opened XBMC and found that my CPU seems to be using one core for about 5 seconds, then swapping to the other core and then back again. This seems really odd.

System Specs incase this helps:

Intel C2D E6750 @3.2GHz
G.Skill 2GIG DDR2 800
Gigabyte P35-DS3
Nvidia 9600GT Palit Sonic OC Edition
WD 500GIG SATAII Green HDD

I beleive drivers etc are all correct however if anyone has some straight forward things that need checking or where to go from here it would be really appreciated.

---

### Post by Rnegade on 2010-07-05
Anyone???

---

### Post by jcoles on 2010-07-06
I just tried it too and had the same result: very laggy response to both keyboard and mouse. If I persist and solve the problem, I will post here. 

Right now, I'm not sure how far I will go. A friend of mine showed me movie trailers on his Windows 7 installation of XBMC and it looked great, so I thought I would just get the program for my Linux box. (You'd think I would know better by now!) 

My friend never said anything about XBMC being so complicated to set up. I got an add-on called Trailer Addict installed and I can see movie titles, but I can't figure out how to actually view anything.

Are you familiar with XBMC?

---

### Post by jcoles on 2010-07-06
Success! (Well, some, anyway.)

My experience is not a recommended way to do the install, but maybe something in it is useful to you or to someone else.
 
Did you install the libvdpau1 nvidia-185-libvdpau packages? 

My installation was working, but laggy without them. When I installed the packages, XBMC would only give me a message that it needed OpenGL and then quit. 

I couldn't figure out how to install/enable OpenGL, so I decided to remove the packages that I had added. On reboot, X (the graphic display manager) wouldn't start. So I rebooted into Recovery Mode, low-resolution graphics. I went to System > Administration > NVidia X Server Settings (I must already have a driver?), which complained that I needed to run the command 'nvidia-xconfig' as root and then restart. So I did.

Now there's normal response to the mouse and keyboard. I viewed some movie trailers, but if I try to view trailers found by doing a search, nothing happens. But, it's progress.

Still find the interface hard to figure out.

---

