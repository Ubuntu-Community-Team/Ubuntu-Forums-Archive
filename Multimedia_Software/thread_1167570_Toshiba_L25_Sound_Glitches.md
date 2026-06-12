---
title: "Toshiba L25 Sound Glitches"
date: 2009-05-23
forum: Multimedia Software
---

### Post by ooZAFLE on 2009-05-23
I have a fresh install of Ubuntu 9.04 on a Toshiba L25 S121 laptop and everything works fine but the sound, the sound will play fine for up to 15 seconds then start echoing and glitching out.

snd-atiixp is the sound module it is using but seemed to be competing with snd-atiixp-modem which I blacklisted. Running alsamixer shows that its trying to use an OSS module, but I've been unable to get it stick to the ALSA module I need. Everything in sound is switched to pulse and pulse shows that it is working.

lspci, shows that it is running fine expect it displays

"ati IXP rev2 unknown codec"

I've attempted methods for correcting this, With no luck.
i.e. "snd-atiixp ac97_codec=0"
in /etc/modprobe.d/alsabase.conf

I can't seem to get this laptop to stop glitching, If anyone has a method or advice for me to try it would be greatly appreciated. Thanks a lot in advance!

---

### Post by xc3RnbFO8P on 2009-05-23
Typo?
> i.e. "snd-atiixp ac97_codec=0"
> # for soundchip snd_atiixp
options snd-atiixp ac97_codec=0
and in **/etc/blacklist-modem.conf**
> blacklist snd-atiixp-modem

---

### Post by ooZAFLE on 2009-05-23
> # for soundchip snd_atiixp
options snd-atiixp ac97_codec=0 

yes thats what i was referring to. and I've already blacklisted snd-atiixp-modem, I just forgot to mention it.

I've come across a fix, If i remove "tsched=0" from "load-module module-hal-detect" in "/etc/pulse/default.pa" to re-enable glitch free audio it resolves my problem leaving me with only skips at the end of audio files. It is annoying and can most likely be resolved with some tweaking but its better then no audio at all. I'm not sure if this is the best way to fix this problem but it seems like a step in the right direction. Suggestion on fixing the skipping?:)

---

### Post by ooZAFLE on 2009-05-23
the majority of the crackling/skipping is resolved after changing

```
default fragments = 8
```
to
```
default fragments = 4
```
in 
/etc/pulse/daemon.conf
in case anyone else has this problem. 

What appears to be the main launchpad for this issue is [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/336965](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/336965).

:p

---

### Post by ezely on 2009-07-28
Hi,
Thanks it helps for a toshiba m40-307 with ATI Technologies Inc IXP SB400 AC'97 Audio Controller

Youre Sincerely

---

### Post by ezely on 2009-08-04
After a couple of day, the Sound will be repair. But as the sound have a problem, then it disconnects the Atheros Wifi card.
At this time the only solution is to set noapic on the boot ...

---

