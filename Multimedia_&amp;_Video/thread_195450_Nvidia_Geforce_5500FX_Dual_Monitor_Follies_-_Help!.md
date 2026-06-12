---
title: "Nvidia Geforce 5500FX Dual Monitor Follies - Help!"
date: 2006-06-12
forum: Multimedia &amp; Video
---

### Post by smittyinside on 2006-06-12
Alright - I lugged my old Dell P780 17" monitor back up to my house from my parents place to use as a secondary monitor. I've got the Nvidia proprietary driver installed and it initializes just fine. However, I'm not getting the desired results.

The card in question (eVGA 256 MB GeForce 5500FX AGP) has both a DVI and VGA port in the back. When both are plugged in, Xorg sees the VGA (old monitor) and doesn't output to the DVI (Dell 1801FP). If I unplug the VGA, the flat screen DVI output works fine. At the moment, I'm using my only usable xorg.conf setup, which goes to the VGA monitor.

Now, on to what I want to do - I want to have a dual head setup with my Dell 1801FP flat panel as the main monitor and the Dell P780 as the secondary monitor. I've attached a diagram (overkill, but I figured I'd test out OpenOffice Draw for kicks) of what I want to do. I've also attached a text copy of my xorg.conf file. 

I've tried following the guides and all I get is X not starting or having it hang. Does anyone know, based on my description, what I need to do to get Twinview working?

Thanks in advance!

---

### Post by smittyinside on 2006-06-13
Bump for the morning crew.

---

### Post by smittyinside on 2006-06-13
Anyone? :confused:

---

### Post by BLHansen on 2006-06-13
Maybe you gave me a clue to my Evga FX5500 128Mb ram cards problem.
I only use the Analog VGA connector and it only will do VGA 640x480 16 colors. I hope we both get more clues to the problem here.
Update on my situation. It is the combination of my KDS 15" LCD monitor and the eVga FX5500. My newer Viewsonic LCD on the FX5500 is fine as is the KDS on a different computer with an FX5600. Sorry I didn't have anything to add to your problem, but you did give me the added idea to trace my problem.

---

### Post by smittyinside on 2006-06-13
Well, finally got it going. :p  Turns out that nvidia-xconfig --twinview --xinerama actually got the dang thing to do it, without kooky xorg editing. Go figure. Might be a suggestion to others with the same problem.

---

