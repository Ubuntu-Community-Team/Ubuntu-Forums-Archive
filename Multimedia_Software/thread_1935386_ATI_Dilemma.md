---
title: "ATI Dilemma"
date: 2012-03-04
forum: Multimedia Software
---

### Post by fOmey on 2012-03-04
Welcome to my ATI dilemma !

Before I begin:

GFX: Radeon HD 5770 aka. Juniper
OS: Pinguy OS 64bit (latest)


So what is this dilemma of mine might you be wondering ? OK, Lets begin..



I get a more fluent visual display with open source ATI drivers. Although no HDMI audio! Which sucks.. I have made sure all the output settings are set to HDMI, 

aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


With propriety ATI drivers I get decent visual with HDMI audio.

Although the audio drivers goes into some type of sleep mode ? You might be wondering what I mean by this.. When no audio is playing the audio signal via HDMI is lost so when audio begins to start playing agian causes like 2 seconds of silence and a notification on the TV to appear saying that it has detected HDMI signal once agian!



This is extremelyyy annoying although better then no audio at all!



Soooo what Im hoping to do is either fix this silly pause with the propriety drivers or get some sort of open source HDMI drivers !

Preferably open source HDMI drivers as I personally think the opensource visual drivers are alot more smoother.. BUT HEY IM NOT FUSSY !


So if you could be ever so kind so resolve this silly issue for me I would be forever grateful.

Cheers.

---

### Post by Yellow Pasque on 2012-03-04
You need a 3.3 kernel for open-source HDMI audio on RadeonHD 5000-series. [http://www.phoronix.com/scan.php?page=news_item&px=MTAyNDY](http://www.phoronix.com/scan.php?page=news_item&px=MTAyNDY)
Don't forget to add radeon.audio=1 to your boot line (in /etc/default/grub).

---

### Post by fOmey on 2012-03-04
> **Temüjin said:**
> You need a 3.3 kernel for open-source HDMI audio on RadeonHD 5000-series. [http://www.phoronix.com/scan.php?page=news_item&px=MTAyNDY](http://www.phoronix.com/scan.php?page=news_item&px=MTAyNDY)
Don't forget to add radeon.audio=1 to your boot line (in /etc/default/grub).

This is epic news, Iv got no idea how to flash it tho !..

---

### Post by 2F4U on 2012-03-04
Not sure what you mean by "flash it", since radeon.audio=1 is a kernel parameter, which can be added to the grub kernel line.

---

### Post by fOmey on 2012-03-04
Well 3.3 is still RC if im not mistaken ? So I would have to update my kernel ?

EDIT: So I updated my kernel to 3.3rc5, Remove ATI propriety drivers, HDMI worked. With the same bug as the propriety drivers ! Arghhhh dam it.
Beging to think this isnt a driver issue, but something more.. I just wish 3.3 was more stable so I could run some proper tests...

EDIT 2: Brewing up another kernel update using "make oldconfig" this time around.. hopefully its a little more stable..

EDIT 3: Same issue, HDMI audio goes to sleep.. I even tried Ubuntu 10.04 which supposedly was most compatible with propriety drivers same issue there. If only there was a way to make them run in realtime!

EDIT 4: Figured out a way to get it to run in realtime, finally its a work around but eh better then nothing..
The solution is to keep the channel open by looping a silent sound.. no performance issues whats so ever!

Menu -> Startup Applications -> Add -> Command "aplay -c2 -r48000 -fS16_LE < /dev/zero &" -> Save -> Reboot

---

