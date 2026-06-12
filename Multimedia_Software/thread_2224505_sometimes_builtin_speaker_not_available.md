---
title: "sometimes builtin speaker not available"
date: 2014-05-16
forum: Multimedia Software
---

### Post by frank-wagner-p on 2014-05-16
ASUS Laptop with builtin speaker, Xubuntu 14.04 LTS

Most time I need no sound, so I don't recognize it immediatly that my speaker are not found by system.
If I need my speakers, sometimes sound is working, sometimes not :(
If not, I recognized linux didn't found my builtin speaker, see attached screenshot
[ATTACH=CONFIG]253222[/ATTACH]

maybe some trouble with other devices?
but how can I check this?
any tips and hints are welcome

---

### Post by frank-wagner-p on 2014-05-21
Problem was reproducable
after _each suspend_ speaker were unavailable suddenly **and** headset plugged in :confused::confused:
after a reboot speaker available und no headset plugged in
seems to be a known bug of ubuntu 14.4, because I got an update today for pulseaudio components and now problem is gone :)

---

### Post by frank-wagner-p on 2014-05-22
after some suspend/resume problem back again
Speaker are unavailable and invisible headphones are plugged in :twisted:

why Linux always thinks that headphones would be plugged ??

---

### Post by alfh on 2014-11-16
A workaround, not a fix, but connecting and disconnecting the headset made speakers available again. Ubuntu Studio (xubuntu) 14.04

---

### Post by frank-wagner-p on 2014-11-17
no, this don't work for me :(

---

### Post by Francis_Thrien on 2015-02-12
> **frank-wagner-p said:**
> Problem was reproducable
after _each suspend_ speaker were unavailable suddenly **and** headset plugged in :confused::confused:
after a reboot speaker available und no headset plugged in
seems to be a known bug of ubuntu 14.4, because I got an update today for pulseaudio components and now problem is gone :)

I'm experiencing the same issue on lubuntu 14.10, running on an older c2d-based hp elitebook. Does a bug report exist?

---

### Post by valvarexart on 2015-06-03
I'm experiencing the same issue on Ubuntu studio 15.04.

---

