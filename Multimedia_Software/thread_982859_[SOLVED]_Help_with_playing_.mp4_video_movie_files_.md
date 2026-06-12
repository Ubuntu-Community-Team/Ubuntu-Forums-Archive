---
title: "[SOLVED] Help with playing .mp4 video movie files on ubuntu 8.1"
date: 2008-11-15
forum: Multimedia Software
---

### Post by linux32_user on 2008-11-15
The .mp4 file doesn't play and the movie player checked the plugins and nothing was found except the mp3 and libavcodec packages, it doesn't play it even then, how to play it? please help.

---

### Post by xc3RnbFO8P on 2008-11-15
Read this (if you haven't):
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by linux32_user on 2008-11-15
OK, thanks, it played after i pasted these commands in the terminal

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

And then after it installed the repository for the medibuntu i pasted this

sudo apt-get install libdvdcss2

then it played. But still i am new to linux, if I did something wrong or like degraded the system's efficiency by writing the above commands or not in proper order or whatever, then please give some suggestion.

---

### Post by binbash on 2008-11-15
> **linux32_user said:**
> OK, thanks, it played after i pasted these commands in the terminal

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

And then after it installed the repository for the medibuntu i pasted this

sudo apt-get install libdvdcss2

then it played. But still i am new to linux, if I did something wrong or like degraded the system's efficiency by writing the above commands or not in proper order or whatever, then please give some suggestion.

there is nothing wrong.

---

