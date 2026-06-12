---
title: "Only &quot;Dummy Output&quot; sound availabile, pacmd list-cards shows 0 cards. lspci shows 1"
date: 2018-07-16
forum: Multimedia Software
---

### Post by jcdoe on 2018-07-16
[http://www.alsa-project.org/db/?f=5ca64d3f949dcf7e4201aaa35ddd37aab65f031e](http://www.alsa-project.org/db/?f=5ca64d3f949dcf7e4201aaa35ddd37aab65f031e)

Here's the output of alsa info

As you can see, there's an audio device listed under lspci, however, pacmd shows 0 available cards.

Sound hasn't been working since i upgraded the motherboard on this machine earlier today. Any help would be appreciated!

---

### Post by jcdoe on 2018-07-17
I fixed it. The GIGABYTE GA-H270N-WIFI motherboard has a bad bios revision. Mine came with revision F7 installed. Flashing revision F8d resolved the issue immediately.

Screaming this for SEO reason:[h=1][FONT=inherit]
GIGABYTE GA-H270N-WIFI[/FONT][/h]

---

### Post by jcdoe on 2018-07-17
Also for SEO purposes: 
CORB reset timeout#1, CORBRP = 0
no codecs found!
snd_hda_intel

---

