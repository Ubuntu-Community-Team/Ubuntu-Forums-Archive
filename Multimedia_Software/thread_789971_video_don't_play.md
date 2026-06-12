---
title: "video don't play"
date: 2008-05-11
forum: Multimedia Software
---

### Post by oric on 2008-05-11
My ubuntu does not play any video format I use an ATI graphics card with hardy heron please help on how to make me have them play

---

### Post by hermes0710 on 2008-05-12
> **oric said:**
> My ubuntu does not play any video format I use an ATI graphics card with hardy heron please help on how to make me have them play


Open a terminal and type (in order to add the medibuntu repositories):

```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

Then install the missing packages:

```

sudo apt-get install w32codecs libdvdcss mplayer

```

and try opening a video through kaffeine or totem-xine or mplayer

---

