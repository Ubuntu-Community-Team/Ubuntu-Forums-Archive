---
title: "Samsung P2370HD HDTV/Monitor resolution"
date: 2009-10-06
forum: Multimedia Software
---

### Post by rggavubt on 2009-10-06
I just bought a Samsung P2370HD 23" HDTV/monitor that I connected to my PC via DVI-D to HDMI.  It is showing up as a 7 inch monitor and the resolution is too big.  The viewing area is using only about a fourth of the monitor size.  I need the xorg.conf settings for the monitor section.  Has anyone set up the xorg.conf for this LCD monitor.  I using Ubuntu 9.04 and the built in motherboard Intel 82852/82855 GM/GME integrated graphics controller.  I'm running a resolution of 1280x960 in Windows XP Pro for this monitor.

---

### Post by the_legendary_saiyajin on 2009-11-20
Hi i am having the same problem with my 40 inch Samsung using a HDMI connector. Im using an ATI HD Radeon 4830 as my graphics card and usually run 1920x1080 in both my windows vista and windows 7 partitions. Can anybody help?

---

### Post by orlanz on 2009-11-26
I am having a similar issue with an ATI Radeon 3300 and  50in Samsung (mod# HL50A650).  For me, Ubuntu says I got a **72inch** Samsung and all sides cut off 1/2 inch when using the HDMI port.

Doing some digging, I ran upon overscan, but they all seem to involve Nvidia, and DVI to HDMIs.  Any one got a clue on how to fix this?

So... BUMP and thanks in advance for any help.

---

### Post by steefjeqv on 2009-11-27
Hi,

Maybe this will help (post nr.4 and 6) :

[http://ubuntuforums.org/showthread.php?t=1254227&highlight=samsung+overscan]("http://ubuntuforums.org/showthread.php?t=1254227&highlight=samsung+overscan")

Greetings,
Steven

---

### Post by the_legendary_saiyajin on 2009-11-27
I fixed my problem with mine by installing the latest ATI drivers from their website for linux. Now the picture is correct through the HDMI.

---

### Post by orlanz on 2009-11-28
SOLVED.

Thanks steefjeqv!  That link helped out quite a bit and it was a TV issue, not Ubuntu.

The solution from the link:
1) Switch to the 2nd HDMI port on the TV (on mine it was the 3rd HDMI/DVI) 
2) Rename the source to "PC"
3) You might have to do, Samsung Menu -> Picture -> Picture Options -> Size -> Wide TV.

Odd TV thing, but that ended up making the screen look just like in VGA mode.  But now, I got my audio going through the HDMI too.  I also updated to the proprietary ATI drivers, but don't know if that helped.

Thanks again.

---

