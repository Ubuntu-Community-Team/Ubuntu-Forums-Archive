---
title: "Beep doesn't work; alsamixer cannot open mixer: No such file or directory"
date: 2011-12-24
forum: Multimedia Software
---

### Post by v_mil on 2011-12-24
Dear Members!
I need beep to know that very long calculation is over. I use standard system beep in LibreOffice as a simplest way. It normally works on Ubuntu 10.04 and 11.10. But on Ubuntu 11.04 beep doesn't work. Ubuntu login sound plays every login, audio files/CDs, videos, windows events sounds also play normally. I try to start alsamixer in terminal:  ~$ alsamixer cannot open mixer: No such file or directory There is no result after one day of googling, reinstalling alsa to Advanced Linux Sound Architecture Driver Version 1.0.24, reverting to 1.0.23 etc. :confused:. There is no bark trying to press invalid key in terminal. In 11.04 and 11.10 I hear a bark trying to press down or right arrow key at the end of line.

PC: Acer Extensa 5620Z with embedded Intel HD Audio. This card is blacklisted in /etc/modprobe.d/blacklist.conf: blacklist snd-hda-intel
Also external USB speakers connected to USB port through USB HUB. I tried to re-enable Intel internal sound but it didn't help.
I have two sound cards: Internal Intel HD Audio
Please help me.
Viktor.

---

