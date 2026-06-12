---
title: "Asus Pundit P4-P5N9300, no digital sound (SPDIF, IEC958, optical)"
date: 2009-10-16
forum: Multimedia Software
---

### Post by Villu on 2009-10-16
Hi,

Trouble getting sound from the integrated optical out on the Pundit P4-P5N9300. (nVidia MCP79, Realtek ALC1200 Audio)

I'm using Ubuntu Jaunty AMD64 with default Alsa and Pulse drivers. I have also tried XBMC Live 9.04. The soundcard is detected correctly and "aplay -l" lists the soundcard and the iec958 (hw0,1). 

Analog sound is fine, both in Jaunty and XBMC Live. Optical shows no light pulses when looked at.

Also tried playing movies with AC3 and mp3 files in both VLC and mPlayer, with various settings, such as: AC3 passthrough, selecting audio device, etc.

Here's what I've tried:

Unmuting all IEC958 devices in alsamixer, saving 
sudo alsactl store 0

Adding to: /etc/modprobe.d/alsa-base.conf
options snd-hda-nvidia model=6stack-dig 

Adding to: /etc/asound.conf
pcm.!default {
   type plug
   slave {
       pcm "iec958"
       #pcm "hw0,1"
   }

}

Have tried uninstalling PulseAudio.

Bios has "HD Audio" enabled, no other audio options.

All of the above has been tried in various combinations.

Tried following walkthroughs and noumerous other I found when googling:
[http://www.xbmc.org/forum/showthread.php?t=58216&highlight=ubuntu+sound+optical](http://www.xbmc.org/forum/showthread.php?t=58216&highlight=ubuntu+sound+optical)

[http://ubuntuforums.org/showthread.php?t=1184934](http://ubuntuforums.org/showthread.php?t=1184934)

Have read the "Comprehensive audio troubleshooting guide".

Can anyone help, please?

Cheers, Villu

---

### Post by Villu on 2009-10-19
Apparently it's an intel chip, and not nvidia.

/etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=6stack-dig

Had to reinstall with Ubuntu x86, since XBMC has trouble with AMD64.

---

