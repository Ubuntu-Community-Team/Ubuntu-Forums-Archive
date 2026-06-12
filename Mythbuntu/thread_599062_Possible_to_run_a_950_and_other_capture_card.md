---
title: "Possible to run a 950 and other capture card?"
date: 2007-10-31
forum: Mythbuntu
---

### Post by dougsnell on 2007-10-31
I realize I may be pushing things ... but is it possible to run a Hauppauge WinTV HVR 950 (em28xx) and any other capture card?  I ask because I've been trying to get it working with a Hauppauge dual-tuner PVR 500.  When I do, the 500 simply will not open in Myth's capture card setup (as MPEG-2 encoder card, it shows "Failed to open").  lspci shows it as two multimedia controllers (mpeg-2 encoders, as iTVC16).

I have verified the 500 recognizes when I install it by itself, and the 950 has been happily recording away.  But when I put the two together, only the 950 seems to work.

Am I missing something?  Is there something I should be running through?  So far, I've followed the following link to get to my currently working 950 setup:

[http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html](http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html)

The Feisty instructions worked like a charm, though I did not have the 500 installed when I went through it.

-Doug

---

### Post by superm1 on 2007-11-01
> **dougsnell said:**
> I realize I may be pushing things ... but is it possible to run a Hauppauge WinTV HVR 950 (em28xx) and any other capture card?  I ask because I've been trying to get it working with a Hauppauge dual-tuner PVR 500.  When I do, the 500 simply will not open in Myth's capture card setup (as MPEG-2 encoder card, it shows "Failed to open").  lspci shows it as two multimedia controllers (mpeg-2 encoders, as iTVC16).

I have verified the 500 recognizes when I install it by itself, and the 950 has been happily recording away.  But when I put the two together, only the 950 seems to work.

Am I missing something?  Is there something I should be running through?  So far, I've followed the following link to get to my currently working 950 setup:

[http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html](http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html)

The Feisty instructions worked like a charm, though I did not have the 500 installed when I went through it.

-Doug

Not with any other V4L card.  Unfortunately, this really just boils down to a political problem upstream when it didn't get merged into V4L due to development styles clashing between two developers.

It really is unfortunate :(

---

### Post by dougsnell on 2007-11-01
That at least explains why I can't get it working ;)

Can multiple 950's be used on the same machine, or can any other devices be added?  I have standard cable (not digital), and I don't have HD.

---

### Post by superm1 on 2007-11-01
In theory you can use multiple 950's.  I can't verify that though since I don't even have one.  I doubt you will get much input out of this forum on it either since you're the first person that voiced something about the 950.

---

### Post by dougsnell on 2007-11-01
What about adding something like an HDHomeRun as a network device?  None of the info I read about it says whether it can do standard cable (I'd think it could).

---

### Post by superm1 on 2007-11-01
Yeah you can do that (mind you it only does hidef or digital stuff)

---

### Post by dougsnell on 2007-11-01
Don't take this as a dumb question ... but is there anything like the HDHomeRun which does standard cable (short of the PVR-500)?

I really like the idea of a stand-alone device with two tuners ... seems a lot easier to maintain.

---

### Post by superm1 on 2007-11-01
There is the plextor convertX, but i'll warn its a bit of work to setup.  Someone stopped in IRC the other day and is working on a howto for it.

---

