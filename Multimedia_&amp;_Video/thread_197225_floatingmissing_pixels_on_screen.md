---
title: "floating/missing pixels on screen"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by linuxguiri on 2006-06-15
the video output on my inspiron 4150 laptop was working fine until a few weeks ago. 

now pixels are missing where they should be and appearing where they shouldn't be. they appear scattered. i've attached some screenshots, so you can see what i mean (you may need to zoom to 100% to see the pixels). 

i did a fresh install of dapper (keeping my /home partition) hoping that it might solve the problem. it didn't.

the problem doesn't occur when i boot into windows so the video hardware isn't faulty.

ideas?

(i have an ati card.)

---

### Post by BitTorrentBuddha on 2006-06-15
That's definitely something wrong with your xorg.conf file, I'm fairly sure there's a way to set that back to standard, but I'm not sure what it is. I'm positive somebody will know how to do that though. I hope I gave you a good start down the path to fixing this, good luck.

---

### Post by linuxguiri on 2006-06-15
thanks for the suggestion. 

i tried following the steps here: [https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

rerunning autodetect. (also tried running aticonfig but it doesn't run on my system.)

unfortunately, i still have the same problem.

---

### Post by linuxguiri on 2006-06-18
changing the xorg.conf settings doesn't seem to impact this problem.

does anyone know what the term is for this "scattering of pixels"? i don't even know how to search for it on the web cause i can't seem to describe it accurately.

---

### Post by pcbroch on 2006-08-07
Have you found your problem?  I too have similar problems on my C640.  Mostly, the corruption apprears on buttons.

---

