---
title: "Ubuntu 10.04 and HD 2400"
date: 2010-05-03
forum: Multimedia Software
---

### Post by foxsick on 2010-05-03
I have  Ubuntu 10.04 and ATI HD 2400. 
My problem: 
 Many times I have been trying to install different (xorg-server, FGRLX, ATI Catalyst) videodrivers to make my stay in Ubuntu better and to get rit the bags.
 But I have been receiving only one result: the loading screen was hanging and system hasn't been loading.
 Every time I have been solving the problem (to make my screen loading how it was before) like this: 
1. Go to recovery mode
2. Go to the command promt
and write
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo aptitude purge ~nfglrx ~nvideo-ati && dpkg-reconfigure -phigh xserver-xorg 
It helps me for all drivers excepting FGLRX driver from Hardware Manager, after it I need to reinstall my system complitely.
If you know or if you have an idea, can you help me?__))
I had tried many solutions which google was offering, but always I had the same issue...

P.S. I will very grateful for any help. Thanks

P.S.2 If I have done wrongs in my text, really sorry. I try to write competent. I will answer on any question.

Thanks!

---

