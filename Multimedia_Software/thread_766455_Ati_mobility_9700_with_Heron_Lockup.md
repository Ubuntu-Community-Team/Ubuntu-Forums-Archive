---
title: "Ati mobility 9700 with Heron Lockup"
date: 2008-04-25
forum: Multimedia Software
---

### Post by Pord on 2008-04-25
Ive just upgraded from gutsy to heron and when I tried to log in again it locks up at random times when the x server starts (i havent even got to see gnome load yet).
So i tried to remove the ati restricted drivers which made no change.
I then tried to fix the xorg file by creating a new one using the xfix and also manually with dpkg-reconfigure xserver-xorg. Both of which didnt help.
I tried to then install the ati restricted driver again with apt-get install xorg-driver-fglrx. Same problem again.
Ive even tried the ati drivers off the ati website which also didnt help.
So i downloaded the live cd with my main pc and tried that and it also crashes on the boot. It makes the boot sound and then freezes. I can still move the cursor but nothin else happens.

When I look at the xorg file with vi or nano all i get under the device section is:

Section "Device"
   Identifier     "Configured Video Device"
EndSection


The old xorg files i used to see had information about the graphics card.

Can any1 help me to fix this please?

System Specs:
Acer Aspire 2026WLMi laptop
Intel Centrino processor
512mb ram
Ati mobility 9700 128MB

---

### Post by Pord on 2008-04-25
I just got onto the desktop with the live CD and then it went into a black screen and couldnt do anything again.


I can get the system working in low resolution mode with VESA but if I try to use the open source or propriety driver it just hangs.

Was working fine in gibbon

---

