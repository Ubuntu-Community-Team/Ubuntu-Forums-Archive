---
title: "[SOLVED] No Sound with SB Live and Hardy"
date: 2008-06-14
forum: Multimedia Software
---

### Post by sevansbr on 2008-06-14
Hello,

As a preface I am extremely new, and don't know much of the terminology that is tossed around by old hands. Please go easy on me.

I have just installed my first Linux OS: 8.04 (Hardy) with GNOME 2.22.2 and 2.2.24-18-generic as the kernel.

From the get-go, the sound has not worked. This is a machine that I have not used in a while, and so I had forgotten what the sound card was. To find out I typed this into the terminal: 
```

aplay --list-devices
```

and I was replied to with:
```
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Live [SB Live 5.1 [SB0220]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 2: Live [SB Live 5.1 [SB0220]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Live [SB Live 5.1 [SB0220]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I have tried working through the comprehensive sound problem solutions guide, but some of the commands didn't seem to work (perhaps because the terminal is different from the shell? I don't know), and the link he gave -- [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) -- no longer appears to have a list of supported cards. That was where I got stranded (step 3).

Can anyone lend a hand? I appreciate the assistance.

---

### Post by Trollslayer on 2008-06-14
Have you tried 'aplay' for the different output devices?

---

### Post by sevansbr on 2008-06-14
Hmmm... is the aplay list of sound cards not what I have shown above? here's another list that I get and the code i use to get it:

```
everyman@FamilyLinux:~$ aplay -L
default:CARD=Live
    SB Live 5.1 [SB0220], ADC Capture/Standard PCM Playback
    Default Audio Device
front:CARD=Live,DEV=0
    SB Live 5.1 [SB0220], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Live,DEV=0
    SB Live 5.1 [SB0220], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Live,DEV=0
    SB Live 5.1 [SB0220], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
surround40:CARD=Live,DEV=0
    SB Live 5.1 [SB0220], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Live,DEV=0
    SB Live 5.1 [SB0220], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Live,DEV=0
    SB Live 5.1 [SB0220], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Live,DEV=0
    SB Live 5.1 [SB0220], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=Live,DEV=0
    SB Live 5.1 [SB0220], Multichannel Capture/PT Playback
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=UART
    MPU-401 UART
    Default Audio Device
default:CARD=V8235
    VIA 8235, VIA 8235
    Default Audio Device
```

Another new development is that I have installed Flash player, and videos that are run by flash (eg. youtube) have sound!

Does that help at all? Any ideas?

---

### Post by sevansbr on 2008-06-14
+

---

### Post by Trollslayer on 2008-06-14
What output connection are you using? Also, if Flash is working then what isn't?

---

### Post by sevansbr on 2008-06-14
Fixed it! The problem was the fact that there is a PCI audio card and a card integrated with the motherboard. In BIOS the motherboard card can be disabled, and then the PCI one takes over and works great!

Found the solution here: [http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)

Thanks for your help, and it was everything besides flash that made no noise: rythmbox, games, movies and Ubuntu start up and shut down noises themselves.

---

