---
title: "Strange sound issue"
date: 2011-07-12
forum: Multimedia Software
---

### Post by SwedishWings on 2011-07-12
Hi,

I have a strange problem with Ubuntu 11.04 (32bit) on MBP 5,1. 
When i play sounds from /usr/share/sounds/ubuntu/stereo, sounds with  a sampling rate other than 44100Hz sound very distorted. For example, **dialog-question.ogg (44100Hz)** sounds fine while **message-new-instant.ogg (48000Hz)** sound really bad. As it turns out, all sounds used by Empathy (message-new-instant.ogg, service-login.ogg, service-logout.ogg) have sample rates of 48000Hz and 22050Hz which makes it a pain to have notifications sounds enabled.

Any ideas are most welcome!

Regards,
Mike

EDIT: Thought it was bitrate at first, but realized it's about the sampling rate.

---

### Post by CatKiller on 2011-07-12
It might be worth having a fiddle with the resampling sections of /etc/pulse/daemon.conf to get something that matches your hardware better.

---

### Post by SwedishWings on 2011-07-12
> **CatKiller said:**
> It might be worth having a fiddle with the resampling sections of /etc/pulse/daemon.conf to get something that matches your hardware better.

Thanks for your reply. 

I tried ffmpeg and a few other with no improvement. Is there a fail-safe value that "should" work?

Regards,
Mike

---

### Post by CatKiller on 2011-07-12
> **SwedishWings said:**
> Is there a fail-safe value that "should" work?

Yes, what's in there by default :) Since it's not working for you, it's probably worth picking something else instead.

---

### Post by SwedishWings on 2011-07-12
> **CatKiller said:**
> Yes, what's in there by default :) Since it's not working for you, it's probably worth picking something else instead.

Hahaha, thanks, so much for the fail-safe... 

Will noodle around some more and post results if I find something that works. 

Thanks!

/Mike

---

