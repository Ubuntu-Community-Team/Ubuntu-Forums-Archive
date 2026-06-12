---
title: "No sound on toshiba Satellite in 9.04"
date: 2009-05-12
forum: Multimedia Software
---

### Post by Rimson on 2009-05-12
**** Lijst van PLAYBACK hardware-apparaten ****
kaart 0: Intel [HDA Intel], apparaat 0: AD198x Analog [AD198x Analog]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0



mereminnehof@mereminnehof-laptop:~$ grep 'audio' /etc/group
audio:x:29:pulse:root:mereminnehof


on my sound config it all said autodetect.


alsamixer is all maxed and not muted :(

---

### Post by Rimson on 2009-05-12
Solved by turning down External amplifier in alsamixer :)

---

