---
title: "Amarok: Xine was unable to init any audio drivers/The device is busy"
date: 2008-08-07
forum: Multimedia Software
---

### Post by pormogo on 2008-08-07
This has me ready to tear my hair out. I can't seem to use amarok for a whole 4-6 hours without having to reboot my computer to get control of my sound drivers back. Randomly when I press stop on amarok, it just never comes back. The next time I hit play it just tells me 

*Xine error: The device is busy*

How is the device busy? I just stopped playback before going to the bathroom and now I'm trying to resume playback!

I closed down amarok and ran a lsof|grep /dev/snd* . Below is the output I got

[i]lsof |grep /dev/snd
pulseaudi  6447 darthbator  mem       CHR     116,16               12178 /dev/snd/pcmC0D0p
pulseaudi  6447 darthbator   17u      CHR      116,0               12214 /dev/snd/controlC0
pulseaudi  6447 darthbator   24u      CHR      116,0               12214 /dev/snd/controlC0
pulseaudi  6447 darthbator   69u      CHR      116,0               12214 /dev/snd/controlC0
pulseaudi  6447 darthbator   70u      CHR     116,16               12178 /dev/snd/pcmC0D0p
mixer_app  6656 darthbator   20u      CHR      116,0               12214 /dev/snd/controlC0
[/i]

????? Why the hell does this keep happening???? I have amarok set to use alsa. My understanding was that old OSS driven applications lock the sound card.

---

