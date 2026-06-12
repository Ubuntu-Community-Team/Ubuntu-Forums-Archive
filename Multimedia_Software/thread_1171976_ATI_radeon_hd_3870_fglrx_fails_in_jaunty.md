---
title: "ATI radeon hd 3870 fglrx fails in jaunty"
date: 2009-05-27
forum: Multimedia Software
---

### Post by peedeeramone on 2009-05-27
buenos dias folks,

ive got a quite annoying problem. ive got kubuntu (and previously ubuntu) 9.04 (jaunty) x64 running with an ATI radeon HD 3870 card. Ive got two 22" widescreens hooked up to it and i want the extended desktop with all the effects, of course.

Heres the problem. when the fglrx drivers are installed and i reboot the machine crashes at gdm (or kdm) login. it doesnt properly render it and the computer halts. no ctrl+alt del or backspace. no response. uninstall fglrx from recovery console and it boots back fine. ive seen alot of users struggling with jaunty and ati cards (big suprise). ive dug around the forums and havent found a real solution.  the open source driver currently isnt cutting it, and i would really like to get this running smoothly.

if anyone has any suggestions, or even links to a helpful thread that would be much appreciated. if you need any info such as system logs or my xorg.conf either before or after fglrx is installed let me know. 

mucho gracias
pd

---

### Post by seedofconspiracy on 2009-05-27
I have the same exact problem.  I can't even stop the X server without crashing the entire system.  Very annoying.  I'm almost on the verge of selling my ATI card and going NVidia.

---

### Post by peedeeramone on 2009-05-28
yeah i used to have an nvidia card on my old system. definitely waaay better linux support. my work uses ati cards and i knew the frustration i had with linux there but i got a really sweet deal on this card.

i used some advice from another thread here:

[http://ubuntuforums.org/showthread.php?t=1133844](http://ubuntuforums.org/showthread.php?t=1133844)

and i did this: > Reinstalled a clean copy of Jaunty.
 After applying updates, I opened Synaptic and removed all xserver-xorg-* useless packages (related to other VGA). Here's the list:
 xserver-xorg-video-all
 xserver-xorg-video-apm
 xserver-xorg-video-chips
 xserver-xorg-video-cirrus
 xserver-xorg-video-intel
 xserver-xorg-video-mga
 xserver-xorg-video-neomagic
 xserver-xorg-video-nv
 xserver-xorg-video-openchrome
 xserver-xorg-video-rendition
 xserver-xorg-video-s3
 xserver-xorg-video-s3virge
 xserver-xorg-video-savage
 xserver-xorg-video-siliconmotion
 xserver-xorg-video-sis
 xserver-xorg-video-sisusb
 xserver-xorg-video-tdfx
 xserver-xorg-video-trident
 xserver-xorg-video-tseng
 xserver-xorg-video-voodoo
 
 After, I installed the xorg-driver-fglrx package and all dependencies, via Synaptic.
 Next step, opened a terminal and typed:
 sudo aticonfig --initial -f
 Finally, I crossed my fingers and reboot. And I'm still here

now i have the fglrx driver working... barely. it slows my system to a crawl (this is a super beefed up system) and i still cant get dual head display to work (though it recognizes all my display outs and such).

whats funny is that my two screens are cloned, and i can flip one upside down, but i cant set up the dual head.

so i guess if anyone can help me from here that would be great. im going to mess around with it some more but unless i get it running im going to revert to the open source for now.

---

