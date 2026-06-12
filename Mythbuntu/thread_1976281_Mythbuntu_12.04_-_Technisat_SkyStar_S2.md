---
title: "Mythbuntu 12.04 - Technisat SkyStar S2"
date: 2012-05-08
forum: Mythbuntu
---

### Post by Kazool on 2012-05-08
Hello @all,

first of all, I am an Linux Newbie and my English is not so good.

Now my Problem,

can anybody tell me how I can install my Technisat SkyStar S2 DVB-S2 Card under Mythbuntu 12.04?

After 3 Weeks I have installed this Card under YaVDR 0.4 with this:

```

0. cd /usr/src
1. sudo apt-get install build-essential linux-headers-generic
2. sudo apt-get install mercurial libncurses-dev
3. sudo hg clone http://mercurial.intuxication.org/hg/s2-liplianin/
4. sudo wget http://www.custler.ru/vdr/SVT-SkyStarS2-…all.run.tar.bz2
5. sudo tar xjf SVT-SkyStarS2-driver-install.run.tar.bz2
6. sudo sh SVT-SkyStarS2-driver-install.run
7. sudo make menuconfig (and disable CX24123)
8. sudo make
9. sudo make install
10. sudo init 6

```

So, after that YaVDR works, but I prefer Mythbuntu. So, how can I use my DVB Card with Mythbuntu 12.04?

Perhaps somebody can write a step by step guide, because I can do c&p.

Thanks for every help!!!!!!!!!!!!!

Kazool

---

### Post by nickrout on 2012-05-08
If you already have the drivers installed (as you describe) then it should just work as a dvb device.

---

