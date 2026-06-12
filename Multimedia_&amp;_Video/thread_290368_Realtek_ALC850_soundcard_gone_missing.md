---
title: "Realtek ALC850 soundcard gone missing"
date: 2006-11-01
forum: Multimedia &amp; Video
---

### Post by TiD on 2006-11-01
Greetings,

As the title says, my onboard sound card seems to have gone missing.

I shall begin from the beginning.

This is pretty much a fresh install of ubuntu 6.05, that was upgraded to 6.10 yesterday-ish, and from that i installed ET.

Now when i tried to install ET, no sound would occur and i would have an error in the ET console with something about /dev/dsp/.  I found something on here that requires some dpkg reconfig of something.  I can't remember what exactly.  I beleive that's what caused my soundcard to go missing. 

I'm still very new to Ubuntu

my aplay -l says:
aplay: device_list:222: no soundcards found...

alsamixer says:
alsamixer: function snd_ctl_open failed for default: No such device

volume control says:
No Volume control GStreamer plugin found and/or devices

Annnd i don't have a default sound card.

So if anyone know how to get my sound card back, that would be muchly appreciated.

edit: oh i forgot to add, i downloaded Realtek ALC850 drivers from realtek.com.tw, and installed them, rebooted, and still no dice.

---

### Post by kwiwiphotography on 2007-02-23
Maybe you have your sound card off in the bios.

thats what i had because in windows i use a creative sound blaster card which is not supported in ubuntu.

---

