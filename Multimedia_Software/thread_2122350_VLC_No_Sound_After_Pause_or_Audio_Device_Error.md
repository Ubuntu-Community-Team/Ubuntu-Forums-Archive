---
title: "VLC: No Sound After Pause or Audio Device Error"
date: 2013-03-04
forum: Multimedia Software
---

### Post by Spiralagnus on 2013-03-04
I seem to have a catch-22 problem with my VLC.  I'm running VLC 2.0.5 and ALSA Audio on Ubuntu 12.10 with XFCE 4.10 and the 3.7.9 kernel.  

When I installed VLC and I paused the video, there was no sound after I resumed play.  I did a little research and changed my audio device (Tools -> Preferences -> Audio -> Device) from Default to my sound card (HDA ATI SB, ALC662 rev1 Analog Default Audio Device).

This solved the pausing problem but caused a new one.  Whenever I try to play a video on VLC while another resource is also using the sound card (say, for instance, I have a YouTube video paused in my browser), I get the error 

[I]**Audio output failed:**
The audio device "front:CARD=SB,DEV=0" could not be used:
Device or resource busy.[/I]

When this appears, either my VLC sound will not play at all or it will play, but when I pause the video, the audio will continue to play for a few seconds and get out of sync.

Any device I choose in my Preferences menu gives me either one error (no sound after pause) or the other (device error).  I would greatly appreciate any help anybody could provide.

---

### Post by Spiralagnus on 2013-03-07
Anybody?  I really like VLC and want to continue using it on my Linux box without fault.

---

### Post by Spiralagnus on 2013-04-15
Over a month later, and I still haven't found a working solution.  Does anybody have any ideas?  Please let me know.

---

### Post by holadebob on 2013-05-11
Have the same problem. I selected Alsa with VLC audio properties. **Audio won't restart after pausing the movie using VLC**. I switched back to Pulseaudio and the audio works fine after pause. Switched back to Alsa, it don't work. A clear error, but no idea where to begin troubleshooting. If, from what I've read is true, it would be cool to use Alsa for less problems with synch. 

Xubuntu 12.04 up to date
Intel i3 driven mb

---

### Post by Thee on 2013-05-12
I had the same problem, until I updated my VLC to the latest version. So you might wanna try that.

---

### Post by aless3466 on 2013-06-05
Hi! I solved this after install the pulseaudio plugin for vlc.

> vlc-plugin-pulse

After install this, go to Ferramentas (tools) -> Preferências (preferences) -> Áudio (audio) -> Módulos de saída (device) and change it to Saída de áudio Pulseaudio (Pulseaudio), this worked for me on Ubuntu 12.04.

Maybe help you!

---

