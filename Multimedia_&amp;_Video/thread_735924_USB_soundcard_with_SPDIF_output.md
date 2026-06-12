---
title: "USB soundcard with SPDI/F output"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by rklauco on 2008-03-26
I have Creative USB soundcard with ID 041e:3040. It works "fine" using snd_usb_audio module.
It is listed in aplay -l as
```
card 1: External [SB Live! 24-bit External], device 0: USB Audio [USB Audio]
```
I can use it with both mplayer and mocp, I just have to force both to use card 1.
And now, here is the problem: I can't control the volume level when connected using SPDI/F.
I know there is softvol plugin for alsa, but I tried multiple setups with no luck.
I read alsa wiki, gentoo wiki, searched this thread and, of course, google for it.
No luck whatsoever.
Can someone, please, help me to set the softvol to control the output of SPDI/F?

I am perfectly aware that I should rather control the receiver volume level  to avoid distortion, but that's a bit complicated...

Here is the aplay -L output for this card:
```
front:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    Front speakers
surround40:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
```
and my current .asoundrc that does not work:
```
pcm.!default {
type plug
slave.pcm "softvol"
}

pcm.softvol {
    type softvol
    slave {
        pcm "hw:1,0"
    }
    control {
        name "SMaster"
    }
}

pcm.dsp0 {
  type plug
  slave.pcm "softvol"
}
```

Thanks for any help.

---

