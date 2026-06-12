---
title: "Help I can't take this annoyance anymore!"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by luc1fersflowers on 2006-09-22
It appears that alsa keeps switching between my ICH6 and my usb SB Audigy NX. It alternates back and forth after every song change. I've searched the forums/web for anything regarding this and I have tried setting up ~/.asoundrc as well as /proc/sound/cards to default to sound card "1" (Audigy NX). With no success. I wish I could turn the sound card off in the bios but I can't. Is this something wrong with amarok? or else? This is literaly the only thing keeping me from using Ubuntu full-time. I need my music!

---

### Post by croak77 on 2006-09-22
Why can't you disable the onboard sound in BIOS?

---

### Post by MetalMusicAddict on 2006-09-22
> **croak77 said:**
> Why can't you disable the onboard sound in BIOS?

> **luc1fersflowers said:**
> It appears that alsa keeps switching between my ICH6 and my usb SB Audigy NX. It alternates back and forth after every song change. I've searched the forums/web for anything regarding this and I have tried setting up ~/.asoundrc as well as /proc/sound/cards to default to sound card "1" (Audigy NX). With no success. **I wish I could turn the sound card off in the bios but I can't**. Is this something wrong with amarok? or else? This is literaly the only thing keeping me from using Ubuntu full-time. I need my music!

I wish I could help.

---

### Post by Jfoard on 2006-09-23
Maybe rmmoding the driver module for the ICH6 will help?  I think it's snd_intel8x0.

---

### Post by ermannobonifazi on 2006-09-23
Do you have some other USB sound device on you computer (like USB cam?)
Sometime happen that Ubuntu change the order of Audio device (is a bug) and as default is choosen a different audio device (like USB Cam).
to check the problem try this command (when you have working audio and when you have not working audio)

cat /proc/asound/modules

check default sound card (tagged with 0). Should be your ICH.

To avoid the problem in the future you can try

sudo gedit /etc/modprobe.d/alsa-base

and put the right index for the sound card (0 for you preferred, -2 for the rest). 
This method is not guaranteed. Same time may fail. 

(someone on the forum says this may depend to have installed more than one linux kernel at the same time, so you can try removing the unused kernel image release. I've not tested this).


To definitively avoid the problem you can (as me) blacklist the usb_audio sound module, but this wil prevent to use the Cam or other USB audio device.

sudo gedit /etc/modprobe.d/blacklist

add one row with:

blacklist snd_usb_audio

reboot and check.
Edit/Delete Message

---

