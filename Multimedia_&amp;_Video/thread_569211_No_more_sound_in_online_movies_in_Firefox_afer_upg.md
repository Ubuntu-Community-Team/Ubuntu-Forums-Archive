---
title: "No more sound in online movies in Firefox afer upgrading alsa"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by victorgreen on 2007-10-06
I upgraded to alsa 1.0.15rc3 last night in an effort to get my usb soundcard working. 


It did indeed make it work. I modified ~.asoundrc to support 5.1 sound and it worked. 

Today while using my laptop on the go (ergo with no usb soundcard plugged in), I tried to play a youtube video. It played great but there was no sound. 

Ive upgraded and installed adobe flash player 9, Ive modded FF to use aoss as suggested by some forums, Ive messed with the /dev directory in an attempt to make it use alsa. Ive followed every fix I could find online, all to no avail. 

Using alsa cvs 1.0.14 as I was before, the sound worked fine in fire fox.

Oh and the most important thing- I get sound in flash in Fire Fox when I run Firefox as root from the command line (sudo firefox) but not when I run it normally.

EDIT- Sound works in movies in FF when I have my usb soundcard plugged in.
          UNLESS I am currently playing something in Amarok or have Amarok open and paused! then ALL system sound DIES and can only be fixed with restart

---

