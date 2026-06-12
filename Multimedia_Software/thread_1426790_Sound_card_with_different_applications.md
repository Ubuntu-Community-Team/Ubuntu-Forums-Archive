---
title: "Sound card with different applications"
date: 2010-03-10
forum: Multimedia Software
---

### Post by woofti on 2010-03-10
OK, I'm not a geek, so please be simple in your replies, thanks!

Hardy.

After I've streamed audio in Firefox, I cannot use Movie Player (or any other player) for mp3s.

After I've used Movie Player (or any other player) to play mp3s, I cannot stream audio in Firefox (youtube etc).

It seems each application won't give up the sound card for the other application to use it.

If I restart Firefox it works.

Is there any way round this? Sometimes I don't want to restart Firefox.

Thanks

woof x

---

### Post by RedSingularity on 2010-03-11
Your sound card is "hogging" the sound stream.  What you need is a sound server to allow hardware mixing.  Install pulseaudio in synaptic.

---

### Post by woofti on 2010-03-12
thanks

---

### Post by woofti on 2010-03-13
It seems I already have pulseaudio installed. Any other suggestions? Is there, for example, a command I could use to free up the sound card manually?

---

### Post by RedSingularity on 2010-03-13
When you have the problem try the following commands.

killall pulseaudio

then.........

pulseaudio & exit

then try your sound again.

---

### Post by woofti on 2010-03-13
Opened YouTube piece
Did as you suggested
Got this:
richard@webbook:~$ killall pulseaudio
richard@webbook:~$ pulseaudio
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_1106_3288_sound_card_0_alsa_playback_0"): initialization failed.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0

Tried Movie Player, got this error:

"Failed to connect stream: Invalid argument"

Any other suggestions?

---

### Post by lovinglinux on 2010-03-13
Open "System >> Preferences  >> Sound" and change the options to ALSA. See if that works.

---

### Post by woofti on 2010-03-13
Yay! it works!
Thanks!
:0)
woof x

---

