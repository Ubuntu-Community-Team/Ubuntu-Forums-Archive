---
title: "Pinnacle PCTV HD 800i no sound in Myth"
date: 2011-03-19
forum: Mythbuntu
---

### Post by hillperson on 2011-03-19
I've looked through the multiple posts here regarding the Pinnacle 800i card and many elsewhere as well, but haven't been able to find anything that works.

I'm running Ubuntu 10.10 with MythTV and am trying to add the aforementioned card to my system.  I already have a Hauppauge MCE-150 that runs like a champ.

Basically, I get a picture when trying to use the Pinnacle, but no sound in MythTV.  I can successfully get picture and sound using mplayer and vlc so I believe I am simply failing to identify the audio device properly to Myth.  I'm having this experience with analog signals.  I do not yet have any digital signals with which to test those capabilities of the card.

Here's my output from arecord -l:
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CX8801 [Conexant CX8801], device 0: CX88 Digital [CX88 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Based on suggestions I've seen here and elsewhere, I believe I need to enter ALSA:default:CARD=CX8801 or ALSA:plughw:1,0 on the audio device setup line for the card in mythtv-setup.  I've tried both of them and several others including ALSA:hw:1,0, ALSA:default:plughw:1,0 ALSA:plughw:1...  In all cases, the mythbackend log mentions failed to open audio device or gives errors about unknown file or hardware.  Am I missing something obvious here?

I realize I'm a dying breed here with the old analog signals, but I very much would appreciate any wisdom you all may have to offer.  If you need any further info, please let me know.

Thanks!

---

### Post by timvdwest on 2011-04-03
I am having the exact same problem with a SAA7134 chipset tuner. I have tried almost everything and I'm starting to go insane!

```

2011-04-04 00:55:38.539 AudioInALSA(plughw:2,0) Error: pcm open failed: Device or resource busy
2011-04-04 00:55:38.577 NVR(/dev/video1) Error: Failed to open audio device ALSA:plughw:2,0
```

Please help!!!

---

### Post by timvdwest on 2011-04-04
I found a solution to my problem, maybe it will help you to. Look over here: [https://lists.launchpad.net/mythbuntu-bugs/msg02848.html](https://lists.launchpad.net/mythbuntu-bugs/msg02848.html)


Hope it helps.

---

