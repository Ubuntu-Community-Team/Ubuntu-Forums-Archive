---
title: "Matrox g450 Dual Head with Ubuntu 8.10"
date: 2008-11-02
forum: Multimedia Software
---

### Post by mbmccurdy on 2008-11-02
Hallo!

Has anybody managed to get dual-head working in Ubuntu 8.10 with a Matrox g450 card? I had tweaked something together with 8.04 but upon upgrading it no longer works. I just wanted to know if anybody has had any success.

---

### Post by nuiop on 2008-11-04
Not yet...):P
I'm also interested in a solution...

---

### Post by kingmadb on 2008-11-04
I have the same G450 problem and am also waiting for a solution

---

### Post by HooDooWitch on 2008-11-06
Same problem here.

Ubuntu 8.04 and 7.10 previously worked with a Benq 22" widescreen and a Belinea 17". I had these running with the Matrox driver, although I did have to set them up as "generic LCD 1680*1050 widescreen" and "generic LCD 1280*1024" to get them to run. Using the actual make and model for each monitor didn't work.

Now on 8.10 it will only run in low graphics mode with the graphics duplicated on both monitors.

Just my 2c.

---

### Post by nuiop on 2008-11-07
I heard that it is possible to get it working by installing 8.04 and then upgrading to 8.10
Has anybody tried this and had success?

---

### Post by HooDooWitch on 2008-11-10
Given that I was previously on 8.04 and upgraded to 8.10, I'd say no. ;)

---

### Post by dejan.info on 2008-11-15
I had to downgrade X to 7.3 from ubuntu 8.04. I works now with fine with dual screen. Ask if you want my xorg.conf

---

### Post by HooDooWitch on 2008-11-19
Yes please. I reverted back to Ubunut 8.04 and it's all working fine, I'd like to go to 8.10 so it would be helpful.

Cheers

Ian

---

### Post by Robstarusa on 2009-01-22
dejan>

Can you post (or mail) your xorg ?  I am trying to set this up. 

Thanks,

Rob

---

### Post by stham01 on 2009-01-28
Anyone have any luck getting dual head g450 working yet with 8.10?  

I just bought this card along with a wide-screen monitor, now have a single 1920x1080 screen but it would be great to have two.

Downloaded the driver but install.sh doesn't work.

xorg.conf appears to be still default.

how to install the driver???

thanks!

---

### Post by prawnpie on 2009-03-10
There's a bug that's documented here:
[https://bugs.launchpad.net/xorg-server/+bug/292214](https://bugs.launchpad.net/xorg-server/+bug/292214)

I tried the solution of installing the Hardy Xorg and I got dual head working with my Matrox G450. Here are the instructions...

[https://bugs.launchpad.net/xorg-server/+bug/292214/comments/20](https://bugs.launchpad.net/xorg-server/+bug/292214/comments/20)

Man, I wasted hours on this thinking my xorg.conf needed to be tweaked but really there was an underlying bug. ugh.

---

