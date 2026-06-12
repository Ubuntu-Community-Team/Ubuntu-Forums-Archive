---
title: "ALSAequal on microphone"
date: 2018-07-01
forum: Multimedia Software
---

### Post by a_guenther on 2018-07-01
Hi,

I am building right now a baby monitor using a Raspberry Pi (based on [https://ivadim.github.io/2017-08-21-fruitnanny/](https://ivadim.github.io/2017-08-21-fruitnanny/),  with some changes). This isn't exactly Ubuntu, but Raspbian is close enough in this case, ALSA commands would work the same, so I try my luck here as I couldn't get any in the RP forum. Hope this is ok...
To cancel out some microphone noise, I was thinking  a simple EQ might help already. So it should go mic -> EQ ->  GStreamer. I managed to install ALSAequal and get an output, but I have  the feeling it does not actually do something. When I set a very low  level to all channels, it is still unchanged.

For the EQ, I followed basically this: [https://scribles.net/enabling-equalizer ... al-plugin/]("https://scribles.net/enabling-equalizer-on-handsfree-sending-audio-with-alsa-equal-plugin/")

snd-aloop is loaded and my .asoundrc looks the same: ```
ctl.equal { 

  type equal
}
 
pcm.plugequal {
  type equal
  slave.pcm "plughw:Loopback,0,0"
}
 
pcm.equal {
  type plug
  slave.pcm plugequal
}
```
  For the GStreamer configuration, I replaced "device=hw:1" with  "device=equal". Shouldn't this do the job, or am I missing something?

My soundcards with the aloop: ```
~ $ cat /proc/asound/cards 
 0 [Loopback       ]: Loopback - Loopback
                      Loopback 1
 1 [ALSA           ]: bcm2835_alsa - bcm2835 ALSA
                      bcm2835 ALSA
 2 [Device         ]: USB-Audio - USB PnP Sound Device
                      C-Media Electronics Inc. USB PnP Sound Device at usb-3f980000.usb-1.1.3, full s 
```

 The last one is the USB microphone...

---

### Post by a_guenther on 2018-07-05
It was actually not working with the EQ, seems I played around with settings, but only after a reboot they had effect. For now I have no output with the EQ setup, still suspecting my aloop...
It runs headless, I have only ALSA, no Pulseaudio etc...

Any ideas?

---

