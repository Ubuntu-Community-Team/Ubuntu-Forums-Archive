---
title: "RF Keyboard to MythTV to MCEUSB blaster?"
date: 2012-05-30
forum: Mythbuntu
---

### Post by anonymousdog on 2012-05-30
(Mythbuntu 12.04 x86_64 with 0.25 and mythbuntu repos)

I've tried using IR remotes but always get upset (and low WAF) due to their marginal responsiveness (i.e., lost key presses, key repeat issues, etc.)  Therefore, I resorted to some good RF mini-keyboard/touchpad units with backlight.  Those work like a charm and allow for broader use of the PC from the couch without bulky mouse/keyboard sets.

It's all great except in the living room where MythTV feeds a Kenwood receiver via optical SPDIF.  Needing to change the volume means having to use the receiver IR remote to control volume (in addition to the mini-keyboard).

I still use an mceusb tranceiver to control a Dish STB; so, the second blaster output is available, and I've been able to build a lirc configuration file for the receiver that works just fine with irsend.  However, I cannot find a way to get MythTV to translate a volume change request into output to an external script (much like irexec would do if I had any interest in resorting to generic IR remotes again).  There is an Audio setup screen in 0.25 that allows one to disable internal volume controls, but it does nothing to advance use of a third-party or external mixer.  I need MythTV to respond to volume change keypresses like (i.e., {,},[,],F10,or F11) by calling an external command/script.

Is there any way to map the volume change events to external scripts (or some other way of accomplishing IR blasting of an external amp for volume change events without using and IR remote and irexec)?

---

### Post by nickrout on 2012-05-30
Well you could use irexec to trigger a script that uses irsend to turn your volume up and down.

Or more simply you could use the software mixerdevice, and have the volume work with mythtv.

---

### Post by anonymousdog on 2012-05-30
Thanks, Nick.

What would trigger irexec?  Doesn't that just respond to IR signals? I'm using a keyboard instead of a remote.

Does the "software" mixer affect the signal level/volume of digital signals passed from the PC over optical SPDIF?

I think I'm going to settle for a xfce keyboard application shortcut for the desired keypresses (esp since *all* PC sound goes through the receiver).

---

### Post by nickrout on 2012-05-30
> **anonymousdog said:**
> Thanks, Nick.

What would trigger irexec?  Doesn't that just respond to IR signals? I'm using a keyboard instead of a remote. Ok so you are using just a bare keyboard, not through lirc, bad idea on my part> 

Does the "software" mixer affect the signal level/volume of digital signals passed from the PC over optical SPDIF?
 yes at the expense of decoding the digital audio and re-encoding it it, so it's not bit for bit passthrough> 
I think I'm going to settle for a xfce keyboard application shortcut for the desired keypresses (esp since *all* PC sound goes through the receiver).That could work too.

---

