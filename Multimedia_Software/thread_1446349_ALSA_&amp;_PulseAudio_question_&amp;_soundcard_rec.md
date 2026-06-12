---
title: "ALSA &amp; PulseAudio question &amp; soundcard recommendation"
date: 2010-04-03
forum: Multimedia Software
---

### Post by destr0y on 2010-04-03
Background:
My onboard soundcard wasn't supported by ALSA (some via chipset), so I played around until I got it working with PulseAudio...  worked fine most of the time, but then I wanted to use a USB headset for Skype calls - but the only device which showed up in Skype, was PulseAudio - there was no way for me to discern between the two sound cards.  Skype would only work if I made the usb headset the default sound device.

So I bought a cheapo SoundBlaster card, which is (supposedly) suppored by ALSA..  it is, but the support seems flakey.   I rebooted this morning, and its doing the hissing thing.

My questions:

1) I'm not interested (well, I am, but its unnecessary) in surround sound, so can someone recommend a PCI soundcard out there which has truly mature drivers for Linux/Ubuntu?

2) Is how I've described PulseAudio above, how it is actually supposed to be?  ie, should I be able to play music through one soundcard, and use another sound device for particular apps (ala Skype)?

I ask these questions mainly because I got my father-in-law hooked on Ubuntu over xmas, and now he wants to use the same Skype setup but his current sound won't let him.

---

### Post by kostkon on 2010-04-04
> **destr0y said:**
> Background:
My onboard soundcard wasn't supported by ALSA (some via chipset), so I played around until I got it working with PulseAudio...
Actually, PulseAudio is just a advanced software mixer (mostly) that sits of top of ALSA. Thus, ALSA had support for your card otherwise your card wouldn't have worked.
> **destr0y said:**
> worked fine most of the time, but then I wanted to use a USB headset for Skype calls - but the only device which showed up in Skype, was PulseAudio - there was no way for me to discern between the two sound cards.  Skype would only work if I made the usb headset the default sound device.
You need to install the PulseAudio Device Chooser utility to be able to do this.
> **destr0y said:**
> So I bought a cheapo SoundBlaster card, which is (supposedly) suppored by ALSA..  it is, but the support seems flakey.   I rebooted this morning, and its doing the hissing thing.
You could check your hardware volume levels by installing and using the *gnome-alsamixer* utility.
> **destr0y said:**
> 2) Is how I've described PulseAudio above, how it is actually supposed to be?  ie, should I be able to play music through one soundcard, and use another sound device for particular apps (ala Skype)
As I wrote above, you need the PulseAudio Device Chooser utility (install it using Synaptic or the software center).

---

### Post by destr0y on 2010-04-04
> **kostkon said:**
> Actually, PulseAudio is just a advanced software mixer (mostly) that sits of top of ALSA. Thus, ALSA had support for your card otherwise your card wouldn't have worked.

Truly weird..  unless I had PulseAudio installed my onboard sound just wouldn't work.  Detected fine, but no sound.   I might go back to the onboard one now that I'm on the latest ALSA drivers and see how it goes.

> **kostkon said:**
> 
You need to install the PulseAudio Device Chooser utility to be able to do this.

Awesome, thanks for this tip!

> **kostkon said:**
> You could check your hardware volume levels by installing and using the *gnome-alsamixer* utility.

Yep, already tried this.   As soon as I put the master volume above -35db, its snakesville for my speakers.

Will report back with my results, in case it helps anyone in the same boat.

---

