---
title: "No fglrx with Radeon 9250 256Mb"
date: 2005-11-09
forum: Multimedia &amp; Video
---

### Post by brj on 2005-11-09
hi all,

my new asus a9250 (ati radeon 9250 with 256 mb) does not work when using the 'fglrx' driver shipped with breezy. the systems hang when x is started and no X.org.log is written. switching to other consoles is also not possible. the card works with 'ati' or 'radeon' driver.

my old card (his radeon 9200 with 128 mb) worked without problems.

see also:
[http://ati.cchtml.com/show_bug.cgi?id=188](http://ati.cchtml.com/show_bug.cgi?id=188)

jakob

---

### Post by brj on 2005-11-12
[QUOTE=brj]hi all,

my new asus a9250 (ati radeon 9250 with 256 mb) does not work when using the 'fglrx' driver shipped with breezy. the systems hang when x is started and no X.org.log is written. switching to other consoles is also not possible. the card works with 'ati' or 'radeon' driver.

my old card (his radeon 9200 with 128 mb) worked without problems.

see also:
[http://ati.cchtml.com/show_bug.cgi?id=188](http://ati.cchtml.com/show_bug.cgi?id=188)

jakob[/QUOTE]


after going back to my old 9200 everything is ok. i did'nt change settings in xorg.conf nor did i change the fglrx-drivers. so to me it looks like a bug in fglrx-drivers shipped with breezy.

jakob

---

### Post by mlomker on 2005-11-12
[QUOTE=brj]after going back to my old 9200 everything is ok. i did'nt change settings in xorg.conf nor did i change the fglrx-drivers. so to me it looks like a bug in fglrx-drivers shipped with breezy.[/QUOTE]

Could be if you're sure the card is good.  You could give the [newer ones]("http://ubuntuforums.org/showthread.php?t=78466") a try if you like.

---

### Post by brj on 2005-11-14
[QUOTE=mlomker]Could be if you're sure the card is good.  You could give the [newer ones]("http://ubuntuforums.org/showthread.php?t=78466") a try if you like.[/QUOTE]

the card works perfectly under winxp. 

testing hardware is yet another reason to keep winxp ;)

jakob

---

### Post by brj on 2005-11-24
[QUOTE=brj]the card works perfectly under winxp. 

testing hardware is yet another reason to keep winxp ;)

jakob[/QUOTE]

after upgrading to the latest drivers for breezy (8.16.20) fglrx works :razz: 

jakob

---

