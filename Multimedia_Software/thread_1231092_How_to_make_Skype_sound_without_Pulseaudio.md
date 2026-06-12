---
title: "How to make Skype sound without Pulseaudio"
date: 2009-08-04
forum: Multimedia Software
---

### Post by stardustdk on 2009-08-04
Hey all.

How do I make Skype audio (primarily front mic) work *without* using PulseAudio in Ubuntu 9.04.

In Skypeforums they say PulseAudio is a no-go....

So please: If you know how to, let me now.

It is a nVidia sound card.

Should I alternatively use another sound card? Or??

Best regards

Stardustdk

---

### Post by 243kof on 2009-08-04
Try selecting your sound card for Sound In, under Skype Options -> Sound Devices. In my case, it is "HDA Nvidia(hw:Nvidia,0)". You can also select this for all Sound Options (Sound Out and Ringing). The downside is that no other application can play sound while Skype is running.

---

### Post by -=hazard=- on 2009-08-04
Or you can use ALSA mixer with nVidia sound card.

---

### Post by kostkon on 2009-08-04
So, selecting *pulse* for *Sound Out* and *Ringing* and your sound card's input for *Sound In* does not work for you?

---

### Post by stardustdk on 2009-08-06
Pulse for sound out and ringing works.

Mic (front mic on desktop PC) does not.

Best regards

Stardustdk

---

### Post by kostkon on 2009-08-06
> **stardustdk said:**
> Pulse for sound out and ringing works.

Mic (front mic on desktop PC) does not.

Best regards

Stardustdk
OK. How many devices are listed in Sound In? Did you try them all? Did you check the volume levels of your inputs in volume control?

---

