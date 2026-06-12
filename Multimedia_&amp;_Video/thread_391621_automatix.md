---
title: "automatix"
date: 2007-03-23
forum: Multimedia &amp; Video
---

### Post by JUka on 2007-03-23
anyone knos how to get the automatix for breezy

---

### Post by dcrowder32 on 2007-03-23
Last night I tried...seems the server is unavailable.  Anybody know when it should be up again?

---

### Post by taurus on 2007-03-23
If I am not mistaken, it's only available for dapper and edgy.

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

In the meantime, you can install whatever you need by hand, though.

---

### Post by jackrobinson on 2007-03-23
> **dcrowder32 said:**
> Last night I tried...seems the server is unavailable.  Anybody know when it should be up again?
They have moved to a dedicated server and its wicked fast (I must add). DNS propagation to your connection will take time depending on how fast your ISP updates its DNS cache. Keep trying. It should be up for you pretty soon.

---

### Post by hetcxp on 2007-03-24
hi, i'm new in Ubuntu and i'm using dapper (just great) and instaled automatix2 for some updates, but i'd like to know if there's some way to burn the packages that the program has downloaded so i can use them in another computer without internet acces.

---

### Post by devils_casper on 2007-03-24
> hi, i'm new in Ubuntu and i'm using dapper (just great) and instaled automatix2 for some updates, but i'd like to know if there's some way to burn the packages that the program has downloaded so i can use them in another computer without internet acces.
check /var/cache/apt/archives folder. all packages are chached in it.

---

### Post by hetcxp on 2007-03-24
i've found them, thanks.

---

### Post by jackrobinson on 2007-03-24
> **devils_casper said:**
> check /var/cache/apt/archives folder. all packages are chached in it.
not all of them.

---

### Post by hetcxp on 2007-03-24
in fact I just need picasa, acrobat reader, openoffice cliparts, openoffice support for spanish and the codecs for audio, video and dvd and it seems to be all there.

---

### Post by devils_casper on 2007-03-24
[QUOTE=jackrobinson]not all of them.[/QUOTE]
hmmm.. could you tell me what is the other location? i never knew that Ubuntu uses two locations for caching files. :rolleyes:

---

### Post by hetcxp on 2007-03-24
I have another question. ok, i've found all the packages and burned them. is there a way to tell the system that install all the packages in the cd? (just like automatix2 does it from internet)

---

### Post by devils_casper on 2007-03-24
No. its not possible. copy all packages in /var/cahce/apt/archives folder of other machine and install packages through apt-get OR 'dpkg -i' command.

---

### Post by jackrobinson on 2007-03-24
> **devils_casper said:**
> hmmm.. could you tell me what is the other location? i never knew that Ubuntu uses two locations for caching files. :rolleyes:

its not ubuntu.. its apt that caches it in that location.. and automatix is much more than just a wrapper for apt. look at the code and you will now what I am talking about.

---

### Post by devils_casper on 2007-03-24
[QUOTE=jackrobinson]its not ubuntu.. its apt that caches it in that location.. and automatix is much more than just a wrapper for apt. look at the code and you will now what I am talking about.[/QUOTE]
you are not getting my point. it doesn't matter what you use. Synaptic, automatix, aptitude or apt-get. **Ubuntu** stores packages in /var/cache/apt/archives folder only.
as i asked earlier, could you tell me where Automatx stores it cache files? i know it stores in archives folder only but i will be delighted if you  prove me wrong. :D

---

