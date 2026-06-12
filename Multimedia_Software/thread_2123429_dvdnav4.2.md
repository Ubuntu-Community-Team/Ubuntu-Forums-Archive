---
title: "dvdnav4.2"
date: 2013-03-08
forum: Multimedia Software
---

### Post by BubbaBlues on 2013-03-08
There is a problem with the latest version of libdvdnav4. Any dvd you copy with k9copy
or dvd95 with a menu will not play on the computer or a home dvd player.  They just choke when trying to read the menu.  
libdvdnav is a DVD navigation library, which provides an interface to the
advanced features of DVDs, like menus and navigation. It contains the VM and
other parts useful for writing DVD players. It's based on Ogle, but was
modified to be used by xine and mplayer.
They used to play perfectly before  4.2.0+201...
 Is there a way to change that file with an earlier version? I've tried several different distros with this version of dvdnav and 
without fail, every dvd burned is unplayable. Every one of them burned with a previous version works fine. I would have thought
some devs would have figured this out by now.:confused:

---

### Post by BubbaBlues on 2013-03-08
If you untick "Keep original menus" in k9copy, the dvd will be playable. But that doesn't change the fact that dvdnav4.2 is broken and will not allow
writing dvd menus. It should be reverted back to a stable version. ](*,)

---

### Post by mc4man on 2013-03-08
If you believe there is an issue then file a bug report

You can may be able to downgrade if desired though I've no idea what release of ubuntu you have, nor exactly what version of dvdnav (4.2.0+201... is not that informative as there were several 2012 releases
(- downgrading would depend on whether the version you wish is ok with some packages that depend on libdvdnav, usually having  with a min. version acceptable

---

