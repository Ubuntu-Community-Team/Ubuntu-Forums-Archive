---
title: "Patched the kernel and now wireless doesn't work :("
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by 1ronlung on 2009-08-15
Hi.

Have been fiddling with Ubuntu for some months now, but am still very much a newbie, so please treat me gently :)

After *hours* of research on the net, I finally found a guide that I thought I could follow in order to patch my mac80211 drivers, for speedier use with aircrack-ng.

It's the lengthly post on [http://mydellmini.com/forum/dell-mini-10-hardware-upgrades/7623-upgrading-wireless-xp-osx-linux-bt4-aircrack-support-3.html](http://mydellmini.com/forum/dell-mini-10-hardware-upgrades/7623-upgrading-wireless-xp-osx-linux-bt4-aircrack-support-3.html) that I followed.

Compiled my mac80211.ko and copied it over the original module.  Didn't make a backup (idiot!).

Now, when I right-click on network manager, wireless is completely greyed out.  No mention of it in ifconfig or iwconfig, either (that's about the extent of my knowledge).

Now, after reading the full post for the patch instructions, somebody has mentioned:
"meanwhile with broadcom you have to get your hands a little dirty to make everything play nice with injection unless you use backtrack beta 4"

It is a B43 card I have in my laptop.

Help please ?

[EDIT]
Oh.. I got the card working originally with the b43-fwcutter tool, btw.
[/EDIT]

---

### Post by 1ronlung on 2009-08-22
Installed the latest kernel and all is well , again.

If anyone has a safe guide for patching mac80211 (or whatever number) for faster injection that's safe, works, and doesn't invloving recompiling loads of source code, please reply :)

---

