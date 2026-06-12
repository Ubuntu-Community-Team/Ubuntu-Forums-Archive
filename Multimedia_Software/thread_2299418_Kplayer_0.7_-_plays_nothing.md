---
title: "Kplayer 0.7 - plays nothing"
date: 2015-10-18
forum: Multimedia Software
---

### Post by Martan1484 on 2015-10-18
Hi,
when I open any multimedia file with Kplayer in Kubuntu 15.04 I get this error message:
```
 Unknown option on the command line: --fontconfig
 Error parsing option on the command line: -fontconfig
 MPlayer2 2.0-728-g2c378c7-4 (C) 2000-2012 MPlayer Team


```
and nothing happens.

Other players (Kaffeine, Dragon, Mplayer) runs normally.

Thanks for help

Martin

---

### Post by mc4man on 2015-10-18
It appears kplayer has no means to edit it's mplayer cli. If you can't find a way to do that then get a real mplayer installed which should remove that dead & should be buried mplayer2
You can build an mplayer package yourself or builds are here, with mplayer dev slowing down new builds are few & far between but contains fairly recent - 
[https://launchpad.net/~mc3man/+archive/ubuntu/mplayer-test](https://launchpad.net/~mc3man/+archive/ubuntu/mplayer-test)
Maybe by 16.04 Ubuntu/Debian will return the real Mplayer

---

