---
title: "KWorld + Hauppauge PVR 150 = Confusion"
date: 2008-03-29
forum: Mythbuntu
---

### Post by dsbw on 2008-03-29
OK, I've swapped out one of my KWorlds with an old Hauppauge PVR 150.

The Kworld is in slot 0. The Hauppauge is in slot 1. I've added the usual stuff for the Kworld:

alias char-major-81 videodev 
alias char-major-81-0 saa7134 
options saa7134 card=90

and added:

saa7134 
saa7134-dvb
saa7134-alsa

to modules.

But when I go into the setup, things are screwy. On the Analog V4L settings, it shows /dev/video0 as UNKNOWN/GENERIC and /dev/video1 as Kworld AtSC110.

On the DVB settings it shows the Nextwave NXT200X for DVB card number 0 and nothing for 1 (which is right, I think).

On MPEG-2 encoder card (which is what I want for the PVR-150, yes?) it has a blank in the Video device and for Probed Info says: "Failed to open".

Any clues?

---

### Post by klc5555 on 2008-03-30
Are the ivtv drivers actually present? About a month ago I added a 150 to an established 7.10 system that already had a couple of pchdtv 5500s, because I gave up on ever getting the analog drivers for the 5500s working correctly.  But I needed to add the ivtv drivers with synaptic before the Hauppauge 150 could be fired up.

Thereafter, the only thing to worry about is the machine swapping the order of /dev/video0 and /dev/video1 or /video2, etc., randomly after cold starts.

---

### Post by dsbw on 2008-03-30
Geez, I don't know. I figured Hauppauge would be set up with minimal fuss.

How do I tell if the ivtv drivers are there?

---

### Post by klc5555 on 2008-03-30
Just pull up your synaptic package manager and search for "ivtv". I suspect you'll find none of the ivtv packages were installed because the card wasn't in your system when you did the original mythbuntu installation.

Mark all the ivtv packages for installation, install them, reboot, and I think you and the Hauppauge 150 should be in business.

---

### Post by dsbw on 2008-03-30
> **klc5555 said:**
> Just pull up your synaptic package manager and search for "ivtv". I suspect you'll find none of the ivtv packages were installed because the card wasn't in your system when you did the original mythbuntu installation.

Mark all the ivtv packages for installation, install them, reboot, and I think you and the Hauppauge 150 should be in business.

Actually, I did a clean install. I don't have anything invested in this box yet, and I really want to understand what I'm doing, so I've probably done dozens of clean installs with different hardware by this point.

Curiously, no ivtv utilities, even though I installed from scratch. Gonna install those and see what happens.

---

### Post by laga on 2008-03-30
The ivtv kernel modules are installed by default. Check 'lsmod' and 'dmesg' to see if they're loaded.

---

### Post by KillerKiwi on 2008-03-30
Some PVR150 need firmware dmesg should tell you if some thing is missing

---

### Post by dsbw on 2008-03-31
No sign of "ivtv" anywhere.

Wha?

---

### Post by dsbw on 2008-03-31
Never mind. Problem solved. (It didn't detect the Happpauge because I hadn't put the Hauppauge in, I had a completely *different* card in there. <sigh>)

---

