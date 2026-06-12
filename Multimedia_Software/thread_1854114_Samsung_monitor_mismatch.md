---
title: "Samsung monitor mismatch"
date: 2011-10-03
forum: Multimedia Software
---

### Post by windowsblows on 2011-10-03
I have an HP G72 laptop with a 42" Samsung HD DLP TV that i plug into for watching movies, video editing and gaming. My setup was working fine until i upgraded from ubuntu studio 10.?? to ubuntu 11.04. Now when i plug in the TV it recognizes it as a 50 inch instead of a 42 and cuts off all of the screen edges, effectively making all of my menus and launchers useless because i can't see them. i've tried playing with the resolution and have tried programs like 'Arandr' and 'Monitor settings' but nothing seems to help. What can i do to get it to "see" the monitor correctly, i don't want to revert back to 10 if i can avoid it, but i will if i have to. thanks in advance for any help.

---

### Post by WasMeHere on 2011-10-03
Do you mean the software program 'Monitor settings' or the buttons on the edge of the screen? Using analog video with a VGA connection, you often have to adjust the screen width and height.

---

### Post by windowsblows on 2011-10-03
I was using the program Monitor Settings, and its not a vga connection its an hdmi.  I can use a vga cable but i'd rather use the hdmi because it also carries the audio signal and the quality is much better than using a 1/8" stereo jack cable.  I can live without it but its frustrating because the older version of ubuntu worked fine.

---

### Post by WasMeHere on 2011-10-03
I see. What video chip and video driver are you using? Could it be that you 'lost' a proprietary video driver during the dist-upgrade?
System -- Administration -- Hardware Drivers

For example, if you have an nvidia chip, you need a proprietary video driver to get good performance (including recognition of screens).

---

### Post by aeronutt on 2011-12-30
I have discovered this exact same problem, except with Dell Vostro laptop.

42" Samsung DLP, is recognized as a 50", cutting off screen edges.
HDMI connection.
Dell Vostro.
i3 Intel processor (w/integrated graphics).
AMD graphics disabled.
11.10.

Any ideas?

---

### Post by quinn_27 on 2011-12-30
I have the same issue on my media box. Intel Atom 32bit in Asrock ION 330HT system. 
I just upgraded to 11.10. I have an LG 47" LCD HDTV 1080p - model 47LH40. First it thought it was 52" and now it does not know. Either way the edges of the display are not visible. I  upgraded the Nvidia drivers but that did not seem to help. 
Any help would be greatly appreciated. Fairly new with Ubuntu. Thanks!

---

