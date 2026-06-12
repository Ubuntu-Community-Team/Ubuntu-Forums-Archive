---
title: "No sound output from DOSEMU"
date: 2011-05-27
forum: Multimedia Software
---

### Post by LinUxaliVe on 2011-05-27
Hello.

Could someone help me with configuring sound in this emulator (application layer?)?

I could run many dos apps straight out of the box after installing it, but I seem to be unable to acquire any type of sound. Midi, SB , FM, ... anything.

Does anyone here know how to initially configure sound for this? I'm currently using a Sound Blaster Audigy SE, which should be sufficient for all of these types of sound output. :confused:

---

### Post by xvan on 2011-12-06
I know I'm doing some Necromancy here, but this post ranks high in google and I couln't find a complete answer, so here it goes:

DOSEMU doesn't have sound because ubuntu dropped the OSS emulation support in Maverick.

There are several ways to get the sound back...


[LIST=1]
[*]In /etc/dosemu/dosemu.conf or ~/.dosemurc add the line "$_sound =(2)". This enables experimental sdl sound, but for me was lagged.
[*]If using pulseaudio run dosemu with pa oss emulation: "padsp dosemu". Works fine for me.
[*]Same but with alsa-oss: "aoss dosemu". It didn't work well.
[*]Recompile the kernel with alsa-oss support, and get the /dev/dsp* device... I was too lazy to try it...
[/LIST]

---

