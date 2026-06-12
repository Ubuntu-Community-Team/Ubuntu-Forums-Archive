---
title: "Nvidia GeForce 6200 TV out is black and white"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by BerlinOliver on 2006-08-23
Hi there,

I just bought a Nvidia GeForce 6200 card with TV-out. I used this guide (from tseliot) to configure it:
[http://www.ubuntuforums.org/search.php?searchid=7671684](http://www.ubuntuforums.org/search.php?searchid=7671684)
and everything works fine, except the colors on the TV. I attached my xorg.conf and my Xorg.log

What wonders me:
With my old TV-card I had colours and the mode was Composite. When I now write Composite in my x.org.conf I got no TV picture. So I changed it to SVIDEO and I got a picture, but only in b/w. Today I was in a computer store, because I thought I use a wrong cable, But they said I have the right one... 

I really have no idea how to fix this problem. I am desperate now, because I use my computer most times to watch videos. Can anybody please help me?

---

### Post by win_zik on 2006-08-23
Just searched around a bit and maybe you need to change some settings on your TV as described here:
[http://ubuntuforums.org/showthread.php?p=1148730&highlight=black+white#post1148730](http://ubuntuforums.org/showthread.php?p=1148730&highlight=black+white#post1148730)

---

### Post by BerlinOliver on 2006-08-24
HI,

thanks a lot for this hint. But I just fgured it out for myself. The signal was the problem. My TV don't understand SVIDEO. So I only got a b/w picture. I had to change it to Composite and I had to buy a new cable. My card gives the information from different cables out. SVIDEO over a SVIDEO-cable and Composite over a chinch-cable. That was the problem. Now a bought a chinch cable and I got color back. (When I pull the SVIDEO-cable out)

---

