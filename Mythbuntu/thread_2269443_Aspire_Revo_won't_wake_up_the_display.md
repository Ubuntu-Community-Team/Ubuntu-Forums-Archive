---
title: "Aspire Revo won't wake up the display"
date: 2015-03-15
forum: Mythbuntu
---

### Post by John_Filion on 2015-03-15
I have a Aspire R1600 (Revo) system that I have used for a couple of years as a front end, and it works well with the NVIDIA graphics, using the vdpau settings.  However, ever since I updated to 14.04, I am having trouble waking up the unit with either a remote control or a keyboard.  I thought this was a problem with the unit going into a power management mode or a screen saver that wouldn't wake up, but I've done my best to disable all of that.  Then, I discovered that I can open a VNC session to the unit, and the VNC session displays the mythtv front end on my laptop.  From here, I can control the GUI, and I can also get to a terminal, but I can't find any command that will wake up the display on the TV.  This symptom would indicate that this isn't a power management issue, and I don't get why VNC gets the display, but the TV display won't wake up.  As I understand it, the Aspire Revo was a popular platform for MythTV front ends a couple of years ago when they first came out, so I am hoping that somebody has seen this problem and can give me some guidance here.

---

### Post by Lester_Burnham on 2015-03-15
Hi,
Sounds like a HDMI issue to the TV. 
Does the TV display come alive again when you move the mouse via VNC? What about when you drop back to the desktop?
Lester

---

### Post by John_Filion on 2015-03-16
No, the only thing that works is to restart it from the VNC.

---

### Post by Lester_Burnham on 2015-03-16
Hi,
So it's connected via HDMI?
It displays ok on the TV when started with the TV on?
Anything special in your xorg.conf?
Lester

---

