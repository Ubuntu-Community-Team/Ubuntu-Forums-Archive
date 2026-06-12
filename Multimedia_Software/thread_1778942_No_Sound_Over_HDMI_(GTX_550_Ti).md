---
title: "No Sound Over HDMI (GTX 550 Ti)"
date: 2011-06-09
forum: Multimedia Software
---

### Post by techmad on 2011-06-09
Hi Guys,

I recently purchased a new video card a GeForce 550 Ti, but I haven't been able to get sound working over HDMI.
I'm running the latest version of Ubuntu (11.04) and have installed the proprietary drivers through Additional Drivers.

```
Linux xbmc 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux
```The card is being picked up by alsa and I've configured Ubuntu to use HDMI in sound preferences:

aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```When I check alsamixer this is what I see:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=194683&stc=1&d=1307656274[/IMG]

ALSA reports that version 1.0.23 is installed, although I thought 11.04 came with version 1.0.24?

cat /proc/asound/version:
```
Advanced Linux Sound Architecture Driver Version 1.0.23.
```I've tried purging ALSA and reinstalling it but it didn't help. Is there anything I can do?
Does anyone know if this card is supported by ALSA properly yet?
I hate the thought of having to go to Windows to get this working :(

Any help is appreciated!

---

### Post by lidex on 2011-06-09
See this thread:
[http://ubuntuforums.org/showthread.php?t=1668737](http://ubuntuforums.org/showthread.php?t=1668737)

---

### Post by Yellow Pasque on 2011-06-10
> **lidex said:**
> See this thread:
[http://ubuntuforums.org/showthread.php?t=1668737](http://ubuntuforums.org/showthread.php?t=1668737)
It looks like s/he might have already seen that thread: [http://forum.xbmc.org/showthread.php?t=102697](http://forum.xbmc.org/showthread.php?t=102697) ;)

---

### Post by techmad on 2011-06-10
Worked a treat lidex, thanks a million I was ready to give up!

The other post was slightly different in that I was using XBMC Live and my card was being detected at all,
so I upgraded to Ubuntu 11 to see if I'd have better luck, I had actually totally forgotten about the link ](*,)

Alls sorted now though so thanks again ;)

---

