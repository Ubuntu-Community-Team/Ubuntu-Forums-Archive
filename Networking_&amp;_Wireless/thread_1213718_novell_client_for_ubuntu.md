---
title: "novell client for ubuntu"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by bcbotha on 2009-07-15
does anyone know if there is a novell client for ubuntu 9.04? i would very much like to run my ubuntu machine at work rather than use windows.
thanks a lot

---

### Post by D8TA on 2009-08-07
I was using openSUSE but have switch to Ubuntu. It is a little rough since openSUSE had a Novell client but I have been trying to use ncpfs but getting errors.

ndslib.c:1051: Invalid start: 1835008 00010000 00010000 00100006
ncpmount: Invalid server response (-330) in nds login
Login denied.

The credentials I am using are correct so just trying to figure this out and I should be good to go. Anyone have any advise? If ncpfs will work that is fine by me I just need a means to access the Netware shares.

Just found a solution - [https://bugs.launchpad.net/ubuntu/+source/ncpfs/+bug/140464/comments/29](https://bugs.launchpad.net/ubuntu/+source/ncpfs/+bug/140464/comments/29)

---

### Post by lykwydchykyn on 2009-08-07
I run Ubuntu on a Novell network where I work.  There is a bug in Jaunty's version of ncpfs that gives the error described.  You can easily work around it by installing Intrepid's version of ncpfs and locking the version.  

I've attempted to use various graphical versions of Novell client for Linux, including "Novel" and the "official" one from Novell, but I couldn't get any of them to work in Ubuntu.  I can connect with ncpfs though, and I wrote some helper scripts to cut down the rather onerous syntax of ncpmount.

Of course I normally don't think about it, because I've got my home and shared directories scripted to mount at login.

---

