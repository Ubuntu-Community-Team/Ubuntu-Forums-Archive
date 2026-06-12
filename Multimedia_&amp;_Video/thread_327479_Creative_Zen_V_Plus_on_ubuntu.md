---
title: "Creative Zen V Plus on ubuntu"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by mkongsfelt on 2006-12-29
Hello

I have been trying to make my new Creative Zen V Plus work on Ubuntu both with gnomad2 and Amarok, but nothing seems to be working. Anyone who can help me with this one?

\mkongsfelt

---

### Post by bapoumba on 2006-12-29
[http://ubuntuforums.org/showthread.php?t=199250]("http://ubuntuforums.org/showthread.php?t=199250")
[http://ubuntuforums.org/tags/index.php/zen/]("http://ubuntuforums.org/tags/index.php/zen/")

Have you checked these threads ? Do you have any error messages ?

---

### Post by oriondlc2000 on 2006-12-29
Wow, if you ever get this to work put me on the list to be contacted.  This would be wunderfull seeing we have 5 creative labs MP3 players in our house.  Sorry I am too new to help with any kind of programing or anything in linux. In fact it is my first day using linux.  best of luck, oriondlc2000

---

### Post by bapoumba on 2006-12-29
> **oriondlc2000 said:**
> Wow, if you ever get this to work put me on the list to be contacted.  This would be wunderfull seeing we have 5 creative labs MP3 players in our house.  Sorry I am too new to help with any kind of programing or anything in linux. In fact it is my first day using linux.  best of luck, oriondlc2000
I have a Zen micro, working fine with gnomad2 :)

---

### Post by Fixxxer on 2006-12-31
I have a Creative Zen V Plus working with gnomad2 by using the how-to from the first link that bapoumba posted.

---

### Post by stitch on 2007-02-12
Hi, I have a Zen V Plus, but I get this error from Gnomad2:

NO JUKEBOXES FOUND ON USB BUS

The command mtp-detect works well (I see the connection icon).
Furthermore, I edited the file /etc/udev/rules.d/libmtp.rules and added the line:

# Creative Zen V Plus
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4152", SYMLINK+="libmtp-%k", MODE="666"

No other changes...
Any ideas ?

Thanks/Stitch :D

---

### Post by Nuance on 2007-07-31
Hey there, I was having the same problem getting my Zen Creative Plus to work then I decided to reset it by jabbing a needle into the small hole just below the power toggle. After doing this it works no problem in gnomad but still not in amorak.

---

