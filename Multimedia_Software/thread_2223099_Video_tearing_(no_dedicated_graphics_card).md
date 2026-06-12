---
title: "Video tearing (no dedicated graphics card)"
date: 2014-05-09
forum: Multimedia Software
---

### Post by troysos on 2014-05-09
[COLOR=#000000][FONT=Verdana]I just build a new HTPC. I have video tearing in XBMC and also VLC and the default Ubuntu video player. I've seen this problem but it seems to be when someone has a dedicated video card which I don't.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I'm on Ubuntu 14.04 and Gotham. i5 Haswell, 8gb ram, asrock 6extreme motherboard. Everything is up to date. Where should I start and thank you!

I know this is normal with a dedicated graphics card but I have not seen a solution with just Intel graphics.[/FONT][/COLOR]

---

### Post by troysos on 2014-05-09
It looks like this solved it.

sudo apt-add-repository ppa:timo-jyrinki/ppa
sudo apt-get update
sudo apt-get install libsdl1.2debian

---

