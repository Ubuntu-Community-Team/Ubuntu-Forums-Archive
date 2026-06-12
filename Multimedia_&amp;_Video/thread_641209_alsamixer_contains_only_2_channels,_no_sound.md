---
title: "alsamixer contains only 2 channels, no sound"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by roto6 on 2007-12-15
I have just installed Kubuntu on my Acer Aspire 5310. In general, it is fine, but there is no sound. I chose alsa in the Kde system settings, sound care is detected (output of lspci -v below), and alsamixer opens up, but showing oly channels "master" and "pcm" with possibility of changeing volume and switching between them, but no unmuting, and no further channels:

&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.14 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: Realtek ID 268                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-42.00, -42.00]                                        &#9474;
&#9474; 

 Maybe, the  other channels are unmuted and therefore the sound is not working, but I cannot get them. I tried sound  via DVD, CD, and mp3, and system internal sounds, but negative. any ideas? Output of lspci:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 012e
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at d0440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

---

### Post by nille on 2007-12-15
This thread could possibly help you:
[http://ubuntuforums.org/showthread.php?t=545318](http://ubuntuforums.org/showthread.php?t=545318)

According to the later post(s) you can install **linux-backports-modules** instead of compiling from source. Try that!

I have not tried it, and if it doesn't work, check out my post about compiling ALSA from source in that thread ([#14]("http://ubuntuforums.org/showpost.php?p=3374613&postcount=14")).


**EDIT:** You probably should change model=toshiba to model=acer, since you're using an Acer laptop.

---

### Post by roto6 on 2007-12-15
thx! still, alsmixer is looking strange with only 5 volume bars, and there exists no /etc/modprobe.d/sound..., but output sound is completely fine now. (using alsa 1.0.15)

---

