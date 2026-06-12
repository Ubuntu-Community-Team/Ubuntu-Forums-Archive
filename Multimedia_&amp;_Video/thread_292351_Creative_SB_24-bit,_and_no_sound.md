---
title: "Creative SB 24-bit, and no sound"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by codypumper on 2006-11-03
I recently installed a Creative Sound Blaster 24-bit. It worked fine until I upgraded to edgy. At that point only sound output worked. Then I followed the comprehensive sound guide, and I've lost both.
  Several programs give me:
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
  Gnome Volume Control gives me: 
No volume control GStreamer plugins and/or devices found.
  What really :-#  is I have a podcast on skype tonight.

---

### Post by codypumper on 2006-11-03
anyone?

---

### Post by bettlebrox on 2006-11-05
Try running alasconf (if it exists on Ubuntu).

---

### Post by codypumper on 2006-11-05
no luck

---

### Post by sebastfr on 2006-11-06
Do you have more than one card on your system?

Can you copy/paste your '/etc/asound.conf' file here?

cheers

seb

---

### Post by codypumper on 2006-11-06
I need some more help now... I rebooted after reinstalling alsa to get an error of /sbin/modprobe ending abnormally. This is a real pain, does anyone have a way to solve this?

---

### Post by sebastfr on 2006-11-07
What actually fails? Can you copy/paste the output (or dmesg)?

seb

---

### Post by Joey French on 2006-11-07
I have a Creative SB 24 as well, do you have integrated sound on your motherboard? Edgy wanted to default to one or the other and switch them constantly.

---

### Post by sebastfr on 2006-11-07
> **Joey French said:**
> I have a Creative SB 24 as well, do you have integrated sound on your motherboard? Edgy wanted to default to one or the other and switch them constantly.

You can setup which one to default to by having something like :

> 
options snd-usb-audio index=0 #my external SB24 usb
options snd-intel8x0 index=1 #my built-in sound card


in '/etc/modprobe.d/alsa-base', and you need to set the 'pcm.!default {}' parameter in '/etc/asound.conf'

I can give you more details if needed...

seb

---

### Post by Joey French on 2006-11-07
sebastfr, what I meant to say is that was how I fixed it. I made this fix a while back, and was hoping to help codypumper if he had the same problem. Thanks, though!

---

### Post by codypumper on 2006-11-07
sebastfr, thing is with the error /sbin/modprobe ended abnormally, it won't boot any further, I have use the second boot option in GRUB

---

### Post by Velotix on 2006-11-08
Hello. I have a very similar problem to you, only worse: [my sound card isn't being detected in the first place](http://www.ubuntuforums.org/showthread.php?t=295177). I stumbled upon this thread and another one looking for a solution, and [perhaps your solution is here](http://ubuntuforums.org/showthread.php?t=140604).

I'm hoping this will solve my problem as well, but because my card isn't being detected at all I doubt it will. Anyway, I hope this was helpful to you. ^^

---

