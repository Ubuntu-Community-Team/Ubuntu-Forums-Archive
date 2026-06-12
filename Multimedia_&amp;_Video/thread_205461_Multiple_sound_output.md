---
title: "Multiple sound output"
date: 2006-06-28
forum: Multimedia &amp; Video
---

### Post by Klemik on 2006-06-28
I'm using TeamSpeak & Enemy Territory, but when I run TeamSpeak I cant hear sound in EnemyTerritory (sound driver is busy). I found on this forum that it is possible with alsa (got ts and xmms working together while xmms played with alsa output). Now I have to set ts driver to alsa (e.g. for oss its /dev/dsp) - but what path is for alsa ?

---

### Post by LordRaiden on 2006-06-29
Have a look at my guide in my signature under _****_[SIZE=2]_**Getting more than one application to use the soundcard at the same time**_[/SIZE]

---

### Post by Klemik on 2006-06-29
It didnt help me :( Even that aoss <program> trick :/ In ts I can set driver to use but I have to give path to it, I tried all alsa, aoss, alsa-oss combinations and didnt manage it to work :/ Et keeps trying to use /dev/dsp (same as ts), and I see no possibility of changing that :/
Any other ideas ?

---

### Post by Klemik on 2006-06-29
ok I found alsa "path" in device listing, but it doesnt work for ts :( Im muted there :/

---

### Post by LordRaiden on 2006-07-02
At the moment, alsa is not natively supported by teamspeak v2 (it is on the table for v3 apparently). I found this link which might prove useful. [http://www.goteamspeak.com/index.php?page=faq&id=3&item=43#q43]("http://www.goteamspeak.com/index.php?page=faq&id=3&item=43#q43")

If it works, post back, and I'll have a link to it in my guide.

---

### Post by Klemik on 2006-07-02
It doesn't work :( Still got "unable to open /dev/dsp"

---

### Post by LordRaiden on 2006-07-02
Yeah, from that error, it is still trying to use the OSS driver. Did you have a look in the gaming central section? I think a few people are getting or trying to get teamspeak to work with their games.

---

### Post by Klemik on 2006-07-27
I have followed this howto:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound)

and it almost worked...
Now ingame I dont have "device or resource busy" but "sound driver too old".
Any ideas how to update (?) drivers. I have SB PCI 128 sound card, and use snd_ens1371 driver module.

---

### Post by LordRaiden on 2006-07-27
I have the guide in my signature...

---

