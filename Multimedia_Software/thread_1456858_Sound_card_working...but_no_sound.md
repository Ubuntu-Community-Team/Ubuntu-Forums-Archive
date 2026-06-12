---
title: "Sound card working...but no sound"
date: 2010-04-17
forum: Multimedia Software
---

### Post by yonkiman on 2010-04-17
Just installed an Asus Xonar DS sound card.  Installed the latest ALSA 1.0.23 drivers.  The new drivers see my sound card just fine:
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DS [Xonar DS], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: DS [Xonar DS], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Alsamixer sees my sound card, spdif and all the analog outputs are unmuted and at 80% or higher.

But I can't get any sound out of speaker-test, vlc, mythtv, Guayadeque, etc.  The weird thing is that when I play something that SHOULD produce music, the spdif output turns on (glows red) and it turns off when I stop playing something.  But my receiver doesn't hear see a signal.  Same for the analog - nothing comes out.

Everything seems configured perfectly (most of the troubleshooting guides/posts I've read are people trying to get to the state I'm already at), but I can't hear a sound - any ideas?

I'm running the latest 64bit version of Karmic on an Intel Core2 Duo.  The on-board audio used to work OK (except for dropping out occasionally, which is why I'm trying the Xonar), but it's now disabled so the only card the system sees is the Xonar.  I thought having just one sound card would make things easier...  Is it possible there's some config file (for the on-board audio) somewhere messing it up?

---

### Post by lidex on 2010-04-18
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by yonkiman on 2010-04-19
Hi lidex,

This may not be exactly what you want, since I re-enabled my on-board audio so I'd have sound, so my HDA Intel is the current/active/working sound card right now.  When I get a chance (it may be day or two), I'll reboot and disable the Intel chipset on the motherboard.  The only difference for the first 3 requests is that with the Intel sound disabled the Xonar shows up as card 0.  "head -n 1 /proc/asound/card*/codec#*" would be the really interesting one to see I imagine.

Thanks for your help!

$ uname -a
Linux mythtv 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: DS [Xonar DS], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: DS [Xonar DS], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Apr 17 2010 for kernel 2.6.31-20-generic (SMP).


$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC889A

---

### Post by Native Dialect on 2010-04-19
Have you checked sound preferences and volume control in order to make sure that all switches (e.g. PCM) are turned up? I know that sounds like a stupid suggestion, but it happens around here more often than not. For some reason, certain volume switches are muted by default, rather than being turned up.

---

### Post by lidex on 2010-04-19
ekoerner on [this]("http://ubuntuforums.org/showthread.php?t=1456739") thread got sound on his xonar ds with an upgrade to alsa 1.0.23.

---

### Post by yonkiman on 2010-04-24
It's working now.  I'd gone back to using the onboard sound, then I messed around with trying a newer alsa ppa (see the [ALSA Upgrade Script]("http://ubuntuforums.org/showthread.php?t=1046137&page=76") discussion).  Then I uninstalled all that, ran the modified 1.0.23 upgrade script again, and my new Xonar DS was cranking out beautiful, glitch-free spdif!

Thanks for everyone who offered suggestions!

---

### Post by lidex on 2010-04-24
Awesome. Can you mark the thread as solved please? [Use 'thread tools', near the top]

---

