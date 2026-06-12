---
title: "ATI HDMI Sound Issues"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by mike.oldfield on 2008-03-18
Hello,

I have setup my ATI Radeon HD 3650 graphics card on Ubuntu Hardy, and it is working well for graphics.

I have a 32" Toshiba TV plugged into the graphics card as my second screen via an HDMI cable. I'm having a bit of an issue with the sound on it though. I have set all my default sound settings on the GNOME sound setup screen (System -> Preferences -> Sound). It works fine in most applications, however I have to mute and un-mute sound for it to actually start playing. If I don't do this, nothing happens.

In Amarok, it's even more fun and games. I can't even get it to play through the HDMI port. The HDMI port appears to use ALSA, but Amarok claims it cannot find any hardware drivers when I force it to use ALSA. If I tell it to autodetect, it chooses OSS and plays out of my hifi speakers instead. Is there any way I can get Amarok to play through the HDMI?

The graphics driver I am using is fglrx, I don't know if this makes and difference to the drivers for sound on the same graphics card.

Thanks,
Mike.

---

### Post by BlueKoala on 2008-03-18
Mute and unmute?
I'll try that.
I'm having the same issue, HDMI sound on a 3650.

The device is recognized, thogh there's no options to adjust volume or anything for that matter in the sounds options.

I've bypassed the issue by running 12' rca extensions with a regular sound jack to rca adapter from my soundcard to my sound system.  Which kinda defeats the purpose of HDMI sound.

I can only hope that alsa/ati/ubuntu dev team can find a way to make things easy for user like me =]

Meanwhile, I'll update this thread if I happen to find anything relevant. Now I just can't wait to go home and see if the mute/unmute will work on my setup =p

---

### Post by mike.oldfield on 2008-03-19
I've noticed that if you play around with the volume control setting on GNOME it lets you change the device. If you change it to the HDA ATI HDMI option i'll give you turn on and off a switch which seems to make it work... until the track changes...

Any ideas if there are any packages that xine would rely on to play through ALSA?

---

### Post by mike.oldfield on 2008-03-22
I'm now using Exaile as it meets my needs just as well as Amarok does, alongside the fact that it works fine with my HDMI port.

---

### Post by TeoLinuX on 2008-03-31
So if drivers and HDMI kinda work with 8.04... which are the differences with Gutsy 7.10? I mean: what should I install / recompile in Gutsy to make it work with radeon 3650 like it works with 8.04?

---

