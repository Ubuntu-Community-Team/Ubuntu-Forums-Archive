---
title: "Ubuntu -- No Sound Icon/Audio/Pulse Audio Errors/Alsa Mixer"
date: 2013-09-05
forum: Multimedia Software
---

### Post by C0R3O5IVE on 2013-09-05
Hey guys! I am having some serious troubles fixing these problems that I am having on my toshiba laptop. I have been digging google and duckduckgo for several hours now. Checking a bunch of different queries regarding the problems I am having, and none of them are working. So now, I decided to come to the supreme lords of the ubuntu forums for advice, as I am now starting my own thread. 

Okay, so ... The problem is many things!

1. No volume control icon on panel
2. Starting pulse audio in terminal returns:
    phox@security-shell:~$ start-pulseaudio-x11
Connection failure: Connection refused
pa_context_connect() failed: Connection refused
    phox@security-shell:~$ pulseaudio
W: [pulseaudio] pid.c: Stale PID file, overwriting.
3. Running AlsaMixer in terminal returns:
  This sound device does not have any controls.  


Okay, so here is the sound controller/driver that I have....
     phox@security-shell:~$ lspci | grep Audio
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)

I have tried many things to fix this... yet no luck! 

Please oh great masters of the ubuntu forums, sprite your wisdom upon me.
Any help is appreciated, thanks a lot!

---

