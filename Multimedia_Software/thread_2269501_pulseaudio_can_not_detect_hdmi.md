---
title: "pulseaudio can not detect hdmi"
date: 2015-03-16
forum: Multimedia Software
---

### Post by yen2 on 2015-03-16
Hi,


I'm working on ubuntu 12.04 with pulseaudio 2.0.
But my ubuntu can't detect hdmi at sound setting dialog.
When I use "aplay -l" command, it will show hdmi is at card 2, device 0.
According to the pulseaudio verbose log(as attachment, [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)),
I saw that pulseaudio is trying to open hdmi from card 1, device 0, 
but card 1, device 0 is for spdif, I don't know why pulseaudio is getting the incorrect card number.
I have tried to reinstall alsa and pulseaudio,
also downgrade pulseaudio to version 1.1,
but it all doesn't work.


In addition, when I play audio by pulseaudio output, 
it will have some strange sound at the beginning 5 seconds,
if I choose alsa for audio output, everything is fine.
So I suppose that my pulseaudio have some problem,
but I don't know how to fix it.


Any advice and suggestions will be greatly appreciated.

Thanks
Yen

---

### Post by Bucky Ball on 2015-03-16
Welcome. Getting back to the Pulseaudio in the repositories for your release of Ubuntu might get rid of the PA noise at the beginning of PA output.

---

