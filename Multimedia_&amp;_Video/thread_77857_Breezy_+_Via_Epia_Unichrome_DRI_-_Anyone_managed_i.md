---
title: "Breezy + Via Epia Unichrome DRI - Anyone managed it?"
date: 2005-10-17
forum: Multimedia &amp; Video
---

### Post by Lem on 2005-10-17
Hmm.. had a few goes at this, and to be honest, all I've suceeded in doing is becoming very familiar with dpkg-reconfigure xserver-xorg every time I kill x.

Found a deb that worked with Hoary, but no go in Breezy. Have also tried the binaries from dri.freedesktop.org. Everything just kills X until I disable DRI.

---

### Post by Rinnan on 2005-10-17
I am in this same situation with an MII 12000.

Eagerly awaiting any information.

:KS

---

### Post by wezlo on 2005-10-17
[QUOTE=Lem]Hmm.. had a few goes at this, and to be honest, all I've suceeded in doing is becoming very familiar with dpkg-reconfigure xserver-xorg every time I kill x.

Found a deb that worked with Hoary, but no go in Breezy. Have also tried the binaries from dri.freedesktop.org. Everything just kills X until I disable DRI.[/QUOTE]
I actually did - but it took a while.

I used the binary snapshots from dri.sourceforge.net ("common" an d "via").  and installed the k7 kernel images and headers in order to compile them (I just ran the install.sh script as root in both dri packages).  Tuxracer runs great (or whatever it's called now).

The only problem I have is that when I boot into the dri enabled kernel - my system freezes whenever I bring up any of my network interfaces!

I wish ubuntu woulda just incorporated this dri module into their kernel so I wouldn't have the headache.  The good news is that 2.6.13 is SUPPOSED to have the via dri module in it - so maybe in the next update we all won't have to suffer...

---

### Post by Lem on 2005-10-19
I tried the same. However, I guess from the fact that you are using the k7 kernel that you're not on an epia board. I found I had to upgrade to the 686 kernel to compile the DRI, but it still doesn't work. If I add it to my xorg.conf, X dies.

As for the 686 kernel issue, I don't know how this places users of the fanless epias with the Samuel and Eden chipsets. These don't support cmov, and thus won't like the 686 kernel much I would have thought.

---

### Post by k4p0w3r on 2005-12-07
Hi all,

Managed to get DRI to work in Breezy 5.10. I made a wiki for this here:

[https://wiki.ubuntu.com/ViaEpiaDriHowto](https://wiki.ubuntu.com/ViaEpiaDriHowto)

---

