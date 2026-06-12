---
title: "Orange mobile internet - no 3G connection"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by laidback82 on 2009-11-04
Hello all! I'm a brand new user to Ubuntu and am finding it pretty good so far. Never having used anything but Windows before I am finding 'Karmic Koala' fairly straightforward. However, I use an Orange mobile dongle to connect to the internet (in the UK). When I used it in windows I connected through the dongle's interface and had it set to only connect through 3G. Now I can't get the interface to work - I connect through the Ubuntu connections manager, but can only get onto a GSM network, which is obviously totally crap. Any thoughts on how to get around this?

Many thanks!

Simon

---

### Post by pdc on 2009-11-05
some folks who used 3G modems successfully on 9.04 now cannot get them to work on 9.10 and there seem to be problems:

possibles
1) get a previous version of Ubuntu eg 9.04 or 8.10 and try that or

2) tell us some information

> lsusb

and 

> tail -f /var/log/messages

you need to open a terminal and copy and paste the commands;

and copy and paste the results back

If you look towards the end of this link

[http://www.linux.com/archive/feature/52729](http://www.linux.com/archive/feature/52729)

you can see what a 

> tail -f /var/log/messages looks like

---

