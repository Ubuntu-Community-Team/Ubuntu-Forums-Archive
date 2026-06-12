---
title: "server install and alsa not working"
date: 2006-01-12
forum: Multimedia &amp; Video
---

### Post by h3avyarms on 2006-01-12
When I install ubuntu by just pressing enter my sound works, but when I do a server install and set my system up the way I want it simply does not work. I un muted it via alsamixer and nothing. Usually thats the only thing I have to do. there is no alsaconf program as far as I can tell so what am I supposed to do? This is a Inspiron 1200 laptop which uses the i810 driver. Please give me some help on  this one. TIA.

---

### Post by FarEast on 2006-01-13
Hello h3avyarms,

I know next to nothing about difference between 'normal' and
'server' setup, but ALSA packages may be missing in the latter case.
(For servers usually do not need sounds.)

Paste outputs of the commands below, please;) .

$ cat /proc/asound/cards
$ dpkg --list alsa-base libasound2

---

### Post by h3avyarms on 2006-01-17
brandon@h3avynote:~$ cat /proc/asound/cards
0 [ICH6           ]: ICH4 - Intel ICH6
                     Intel ICH6 with STAC9752,53 at 0xdfebfe00, irq 16
brandon@h3avynote:~$ dpkg --list alsa-base libasound2
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  alsa-base      1.0.9b-4       ALSA driver configuration files
ii  libasound2     1.0.9-2        ALSA library

---

### Post by FarEast on 2006-01-17
OK:) What happens if you do the following?

```
$ cd /usr/share/sounds
$ aplay startup.wav
```

---

