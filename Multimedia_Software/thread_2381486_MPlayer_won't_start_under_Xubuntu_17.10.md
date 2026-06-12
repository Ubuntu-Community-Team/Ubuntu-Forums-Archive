---
title: "MPlayer won't start under Xubuntu 17.10"
date: 2018-01-01
forum: Multimedia Software
---

### Post by raphaell2 on 2018-01-01
I've installed mplayer-gui under Xubuntu 17.10 to have more options when it comes to media players. When I try to start it, I get a pop up window that says "Error in skin config file at line 6: PNG read error in /usr/share/mplayer/skins/default/main". When I click OK on that window, I get another one that says "Config file processing error with skin 'default'". When I click OK on that one, I get nothing.

I tried reinstalling all mplayer packages, but the problem stays the same. Oh, and the png file the popup window seems to refer to looks perfectly fine to me.

---

### Post by mc4man on 2018-01-01
This has been broken for 4+ years, I've an open bug for that long
[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1218510](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1218510)
you can read thru, there are some manual fixes but I got so sick of this put a fixed mplayer-skins package in a ppa.
I just copied over package for 17.10 & 18.04 so you could use that. (no need to me specifiably rebuild as it's remained the same for 17.10/18/04
[https://launchpad.net/~mc3man/+archive/ubuntu/mplay-skins](https://launchpad.net/~mc3man/+archive/ubuntu/mplay-skins)

ppa gives insrtuctions on how to add ppa but you don't even really need to add the ppa, just download the all.deb & install with apt
Ex. for 16.04/17.04/17.10/18.04, open a terminal
```
wget https://launchpad.net/~mc3man/+archive/ubuntu/mplay-skins/+files/mplayer-skins_3.2.1~xenial_all.deb
```

If now sitting in Home folder simply 
```
sudo apt install ~/mplayer-skins_3.2.1~xenial_all.deb
```

---

### Post by raphaell2 on 2018-01-01
Thank you, great!

---

