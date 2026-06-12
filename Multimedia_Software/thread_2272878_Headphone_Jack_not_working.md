---
title: "Headphone Jack not working"
date: 2015-04-09
forum: Multimedia Software
---

### Post by marco-bore on 2015-04-09
Hello guys, long time has passed since my last time here!
I'm a skilled user and I have some trouble with the jack output on my laptop, speakers works fine.
I've already follow this thread: [http://ubuntuforums.org/showthread.php?t=1774627](http://ubuntuforums.org/showthread.php?t=1774627) but don't work for me.
Here's my alsa output [http://www.alsa-project.org/db/?f=5fc90c29878d9b02197555ad3d78c6ad70ff80a8](http://www.alsa-project.org/db/?f=5fc90c29878d9b02197555ad3d78c6ad70ff80a8)

What can i do? Don't hesitate to ask for further information! Thank you in advance!

---

### Post by dino99 on 2015-04-11
That howto might help you narrowing down this issue

[https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by marco-bore on 2015-04-13
Thanks for your answer!
I followed the guide you suggested me, i attached the file pulseverbose.log at this message.
Here's the output of the file filtered by grep

```

more pulseverbose.log | grep jack
(   0.711|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Mic Jack' succeeded (not found)
(   0.711|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Mic Phantom Jack' succeeded (not found)
(   0.712|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Rear Mic Jack' succeeded (not found)
(   0.712|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Rear Mic Phantom Jack' succeeded (not found)
(   0.713|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Mic Jack' succeeded (not found)
(   0.713|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Dock Mic Jack' succeeded (not found)
(   0.713|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Mic Jack' succeeded (not found)
(   0.713|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Rear Mic Jack' succeeded (not found)
(   0.713|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Internal Mic Phantom Jack' succeeded (not found)
(   0.714|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Dock Mic Jack' succeeded (not found)
(   0.714|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Dock Mic Phantom Jack' succeeded (not found)
(   0.715|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Mic Jack' succeeded (not found)
(   0.715|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Mic Phantom Jack' succeeded (found!)
(   0.716|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Line Jack' succeeded (not found)
(   0.716|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Line Phantom Jack' succeeded (found!)
(   0.717|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Mic Jack' succeeded (not found)
(   0.717|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headset Mic Jack' succeeded (not found)
(   0.717|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headset Mic Phantom Jack' succeeded (not found)
(   0.717|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Jack' succeeded (not found)
(   0.717|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Mic Jack' succeeded (not found)
(   0.756|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Line Out Jack' succeeded (not found)
(   0.756|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Line Out Phantom Jack' succeeded (not found)
(   0.757|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Jack' succeeded (not found)
(   0.757|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Headphone Jack' succeeded (not found)
(   0.757|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Speaker Phantom Jack' succeeded (not found)
(   0.757|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Headphone Jack' succeeded (not found)
(   0.758|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Headphone Phantom Jack' succeeded (not found)
(   0.758|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Jack' succeeded (not found)
(   0.758|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Phantom Jack' succeeded (found!)
(   0.758|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Mic Jack' succeeded (not found)
(   0.784|   0.000) D: [pulseaudio] module-alsa-card.c: Found 3 jacks.
(   0.824|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-jackdbus-detect.so': failure


```

Seem that the module module-jackdbus-detect.so is missing.



[ATTACH]261249[/ATTACH]

---

### Post by dino99 on 2015-04-13
be sure that you have set the bios to 'HD Audio', not AC97, and the jack is well plugged on the mobo (might be the yellow one i suppose)

---

### Post by marco-bore on 2015-04-14
I took a look at the BIOS setup but i didn't find options regarding audio

---

