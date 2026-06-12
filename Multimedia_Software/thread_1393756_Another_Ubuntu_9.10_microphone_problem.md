---
title: "Another Ubuntu 9.10 microphone problem"
date: 2010-01-29
forum: Multimedia Software
---

### Post by jam49 on 2010-01-29
Hi

I have recently installed Ubuntu 9.10 having not previously installed any linux distros Unfortunately, I have problems with the microphone and having looked through many other posts have not found anything that would help.

I have a sound card described as "Ensoniq AudioPCI ES1371" which I believe is a Soundblaster. I also have a sound card built into my motherboard. The microphone works on the onboard sound card but not on the AudioPCI. I would use the onboard sound but it has never worked very well (load white noise).

I have used alsamixer to ensure the volume settings are correct. In Audacity, if I select the soundcard directly rather than pulse the microphone monitor works and recording works for about 1 second only. 

The sound monitor in the volume control does not pick up any sound, nor does the sound recorder. I assume both of these use pulse and therefore the problem is with Pulse rather than alsa.

I have tried all of the settings in the volume control and a range of settings in the pulse configuration programs, which I have installed, but to no avail.

I also tried booting from an opensuse live cd and the microphone still did not work. The microphone works in Windows XP, which I have used up to now. I also tried disabling the onboard sound in the BIOS and then reinstalling both alsa and pulse but this did not fix it.

I would be very grateful for some help as otherwise I will have to abandon my brief adoption of Ubuntu.

Thanks in advance.

---

### Post by jam49 on 2010-01-30
Solved by upgrading pulseaudio to the latest version. I'd assumed (incorrectly) that this would be done by default in the upgrade but apparently not.

---

