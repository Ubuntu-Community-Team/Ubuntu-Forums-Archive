---
title: "Logitech USB 350 Headset not working"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by flyingsolo on 2006-09-05
No sound is coming via this headset.  It is recognized in Device Manager.  Not sure what to do/check next.
Any thoughts?
Thanks

OK--self-serviced with easy fix!  Just reboot and is now working except for the in-line mute and volume controls.  Not sure why this is so.

---

### Post by jessecollins on 2006-11-07
Has anyone else had problems with the Logitech 350 headset on 6.10 Edgy?

Like flyingsolo, the headset was working after the first reboot but now there is about a 50-50 chance that it will be working.  Also, there is a better chance that it will work after a full shutdown and it hardly ever works after a restart.  Weird.

I would love to hear from someone that has had any success with the Logitech 350 headset on Edgy or anyone that could shed some light on the situation.  Thank you in advance.

---

### Post by ErnobmaS on 2006-11-15
Sorry I can't help, but I will second the problem. Logitech 350 headset is not working in Dapper or Edgy (no amount of reboots have ever helped). Would love to use Skype... Any help is much appreciated.

---

### Post by Swab on 2006-11-18
I'm actually running Debian Etch, and not sure of the model of my headset, but it is Logitech USB.  

Same problem, will work on some boots, not on others.  Actually I haven't it hasn't worked at all this evening.

amixer shows that the card is recognised and is the default card.

When I try to play a sound to it from aplay

```
aplay: main:550: audio open error: Device or resource busy
```

---

### Post by Swab on 2006-11-18
Turning off ESD seems to have fixed the problem... obviously far from ideal, but good enough for me!

Edit: OK, a bit premature, after the latest reboot it stopped working again.... aaargh!

---

### Post by ErnobmaS on 2007-03-14
I finally got Skype to work with my headset; not sure what I did, but apparently I happened across the correct settings. Here's what they have to be to work on my system:

For the Logitech Headset 350

SOUND PREFERENCES (in Gnome)
> Sound Events Playback:			Autodetect
Sound Music/Movies Playback:		Autodetect
Sound Audio Conferencing Playback:	USB Audio
Sound Audio Conferencing Capture:	OSS - Open Sound System

SOUND DEVICES PREFERENCES (in Skype)
> Audio System to use:			OSS - 2 devices found
Audio In				/dev/dsp1
Audio Out				/dev/dsp1
Ringing					/dev/dsp1

I hope that helps someone out there.

---

