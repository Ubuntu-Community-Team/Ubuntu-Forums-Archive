---
title: "Distorted sound in VLC and Skype"
date: 2012-01-22
forum: Multimedia Software
---

### Post by Handssolow on 2012-01-22
This posting is mainly for information. Last week I moved my HD over to an Asrock A790GXH/128M motherboard with its VIA VT1708S 7.1 sound. Whilst I was able to play mp3 files with Movie Player when I tried with VLC the sound was distorted and also in Skype. 

After much playing around with the configuration in System Settings>Sound>Hardware, I wasn't making much progress. Sometimes I'd get VLC to play clearly for about 20 seconds then the audio would distort again. Strange though that Movie Player was working fine.

VLC 
The solution I found was VLC's Tools>Preferences>Audio and for the Output module to select "Alsa audio output" rather than "Pulseaudio audio output" (then Save). It worked, I could play mp3 files with VLC.  Audio in Skype initially seemed normal but reverted to being distorted.

Skype
Following advice from qpens (link below), I changed the line in /etc/pulse/default.pa from
load-module module-udev-detect to load-module module-udev-detect tsched=0

After a reboot, Skype>Options>Sound Devices show many other devices than only Pulseaudio. I used the default device for the speakers and the USB connected webcam's microphone. I'm not certain if this is the optimal solution to these issues. It seems to have slowed the PC even though CPU activity in System Monitor is minimal.

[http://ubuntuforums.org/showthread.php?t=1900841&highlight=Skype+sound](http://ubuntuforums.org/showthread.php?t=1900841&highlight=Skype+sound)


Somehow I was expecting audio to be sorted out globally just by configuring Sound in System Settings rather than tweaking the individual applications.

Any comments? Should there be a neater solution?

---

