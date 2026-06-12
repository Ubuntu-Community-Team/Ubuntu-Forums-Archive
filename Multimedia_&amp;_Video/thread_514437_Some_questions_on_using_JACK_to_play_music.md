---
title: "Some questions on using JACK to play music"
date: 2007-07-31
forum: Multimedia &amp; Video
---

### Post by Pogo708 on 2007-07-31
Alright, so I've got a Gateway MT3705 laptop with an SB450 HDA audio device, which as I've gathered from forum posts is destined not to work. Luckily, I also have an M-Audio Jamlab usb audio device, which I'm currently trying to get to work properly. In pretty much any program I can tell it to use ALSA and this device, and sound comes out great. The only problem is I have absolutely no control over the volume; it's locked at max. I'm trying to fix this by running the programs I want to use (REAPER through Wine, Ardour, Audacity, and Audacious, mainly) through JACK, and modify the volume through that. This is the part where I'm clueless as to what to do. Can someone help me out, or suggest a better solution? I'm running the newest version of XUbuntu. Thanks!

---

### Post by fredj on 2007-08-01
Most USB devices can't be controlled through the Alsa mixer. Doesn't the device itself have 
any volume control or don't the sound sources you feed into it have any volume controls?

---

### Post by Pogo708 on 2007-08-01
The device itself doesn't have a volume control, and so far only Audacious has one built in. This wouldn't be too much of a problem, but I'm using this on headphones, and I don't want to risk forgetting about something and blowing out them or my eardrums. D:

---

### Post by fredj on 2007-08-02
Open the Alsa mixer and go to the FIle->Change Device menu. Does your Usb device show up
there?

---

### Post by Nunu on 2008-04-01
> **fredj said:**
> Open the Alsa mixer and go to the FIle->Change Device menu. Does your Usb device show up
there?

Nope i have the same issue.

---

