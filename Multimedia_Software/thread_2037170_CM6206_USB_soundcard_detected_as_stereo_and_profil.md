---
title: "CM6206 USB soundcard detected as stereo and profile dropdown missing"
date: 2012-08-03
forum: Multimedia Software
---

### Post by jamieburchell on 2012-08-03
Hello

I've recently installed Ubuntu 12.04 LTS and have run in to an issue with my external USB 7.1 channel sound device (CM106 chip).

Within "Sound Settings" the device is detected as "CM106 like sound device analogue **stereo**" and the subwoofer and fade sliders are disabled. I've read many references to a hardware tab and/or a profile selection drop down to change the speaker configuration, which apparently should be here, but aren't.

So basically I'm only getting stereo sound and no other controls or options. I've tried editing the pulse audio config to enable more than 2 channels, but this didn't help. I also tried another suggestion which was to install "alsa-hda-dkms" which also didn't help. What am I missing?

Here's a link to the USB device for reference:

[http://www.ebuyer.com/106540-xenta-external-usb2-0-8-channel-sound-card-a-cm106]("http://www.ebuyer.com/106540-xenta-external-usb2-0-8-channel-sound-card-a-cm106")

Thanks in advance for any help you can offer

Jamie

---

### Post by jamieburchell on 2012-08-30
OK, so I have progressed slightly.
 
I found how to change my sound card profile to 5.1:
 
```

$ pacmd
>>> list-cards
>>> set-card-profile 1 output:analog-surround-51

```
 
But now I have a new problem with the sound volume control sliders. When I adjust the balance, the fade slider moves. The subwoofer and output volume sliders are also linked together.
 
Any ideas how to get this working properly?
 
BTW, I'm also completely confused what part the AlsaMixer and pavucontrol can play in this.

---

### Post by jamieburchell on 2012-08-30
I've also noticed that the channels in alsamixer are mapped incorrectly:

Speaker front  = Front
Speaker rear = Center
Speaker side = Rear
Speaker center = does nothing
Speaker subwoofer = does nothing

The "Speaker Test" works as expected for each channel and pavucontrol also controls the correct channels

---

