---
title: "App hijacks soundcard"
date: 2010-03-28
forum: Multimedia Software
---

### Post by trideceth12 on 2010-03-28
Hello all!

An application I am trying to get going on 9.10 takes over my soundcard whenever I run it. I hear a small pop from the speakers and then no application can play sound after that.

The program is: springlobby
My soundcard is: Onboard sound (Asus M4N68T-M motherboard)

I have posted on the application's forum but it seems most of the posters are developers and the advice goes a bit over my head.

> old versions of SL uses SDL audio to access the sound card, make sure SDL audio is set to use alsa+dmix or pulseaudio, if it's set to OSS or alsa with direct card access, it will lock the sound card

if it's a recent version, everything i said applies instead for openal

I have removed pulseaudio but this is not the cause of my problem as it was the same before removal.

full thread is here: [http://springrts.com/phpbb/viewtopic.php?f=20&t=22600](http://springrts.com/phpbb/viewtopic.php?f=20&t=22600)

Thanks in advance.

---

### Post by trideceth12 on 2010-03-29
So does anyone know how to ensure a particular program is using dmix?

---

