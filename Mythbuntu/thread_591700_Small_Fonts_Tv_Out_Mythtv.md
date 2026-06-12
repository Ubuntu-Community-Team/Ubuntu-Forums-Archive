---
title: "Small Fonts Tv Out Mythtv"
date: 2007-10-25
forum: Mythbuntu
---

### Post by djhedges on 2007-10-25
Fonts just too small for certain parts in Myth like the TV Guide, or program information.

I have another box setup for my dad and I fixed that problem before by adding
Option     "DPI" "100 x 100"
in the monitor section of Xorg.conf, but no luck here.

Video card is a Nvidia MX 440

I had to switch to some legacy nvidia drivers that were in the repository because the card is so old.  It fixed the crazy wavy lines the newer drivers had.

---

### Post by napsilan on 2007-10-25
setup->setup->appearance->font size

---

### Post by djhedges on 2007-10-25
Didn't affect mythtv

---

### Post by superm1 on 2007-10-25
two things:

First:
Checkout /var/log/Xorg.0.log to see what DPI it claims to be setting up.

Second:
Checkout "**xpyinfo | grep dot**" to see what comes up there.

---

### Post by djhedges on 2007-10-26
> **superm1 said:**
> two things:

First:
Checkout /var/log/Xorg.0.log to see what DPI it claims to be setting up.

Second:
Checkout "**xpyinfo | grep dot**" to see what comes up there.

dj@dj-server:~$ cat /var/log/Xorg.0.log | grep DPI
(==) NVIDIA(0): DPI set to (100, 100)
(WW) NVIDIA(0): Option "DPI" is not used
dj@dj-server:~$ xdpyinfo | grep dots
  resolution:    100x100 dots per inch
dj@dj-server:~$

Still seems like they're kinda small, I guess I could try 150x150.

---

### Post by thematadorme on 2007-12-14
I've just posted a solution that might help you.
[http://ubuntuforums.org/showthread.php?t=640389]("http://ubuntuforums.org/showthread.php?t=640389")

---

