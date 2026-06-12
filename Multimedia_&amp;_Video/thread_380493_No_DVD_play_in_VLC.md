---
title: "No DVD play in VLC"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by Cannonade on 2007-03-09
OK, I started out doing a search for the problem and found out how to make VLC player my default player for DVDs by typing "gconf-editor" into terminal, etc.

However, I cannot get DVDs to play in VLC player. I have no trouble with .mpg files or .avi files. It even plays DivX and Xvid with no trouble at all.

But what will happen is, when I put a DVD into the drive, it will start to play in VLC player, but it will stop straight away.

---

### Post by mac.ryan on 2007-03-09
...of course you have already installed the non-free DVD and multimedia codecs, right?

(If not, an easy way to do it is through Automatix2: [http://getautomatix.com](http://getautomatix.com))

---

### Post by Cannonade on 2007-03-10
Yes, I've installed automatix and it worked wonderfully! I now have DVD codecs and they all play in VLC player. Thanks for that.

---

### Post by naborcoj on 2007-03-24
Hi,
I`ve had the same problem and found it was related with DMA. Than, I enabled DMA to my DVD drive and now it plays smoothly.
You can found a how-to enable DMA here:
[https://help.ubuntu.com/community/DMA]("https://help.ubuntu.com/community/DMA")

---

