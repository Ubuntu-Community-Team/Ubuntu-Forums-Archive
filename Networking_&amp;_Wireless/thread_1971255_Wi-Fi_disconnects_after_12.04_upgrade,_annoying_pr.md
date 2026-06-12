---
title: "Wi-Fi disconnects after 12.04 upgrade, annoying problem"
date: 2012-05-02
forum: Networking &amp; Wireless
---

### Post by cyberEl on 2012-05-02
Hi,
 i upgrade from 11.10 to 12.04, the first issue i had was the corrupted grub which i fortunatelly solved. 
 Then i noticed that my wifi stick a netgear wg111v3 i used just doesn't work so i tried with another usb stick a tp-link tl-wn821n. This one initially seems to work but after a few seconds the connection goes down,it reconnects after a while, and so on.
 I tried several solutions even installing the latest driver for the tp-link but the problem still exists. I tried a live cd with an ubuntu based distribition which use an older kernel version and both wifi sticks work out of the box. What do you advise me to do? Is this a kernel problem? will it be better if i install an older ubuntu version?

---

### Post by yocta on 2012-05-11
The same thing has happened to me. From memory it also happened when I first installed 11.10 but I can't remember how I fixed it (I think I reinstalled some drivers).

I found this forum on the interwebs that could help:

[http://linuxblog.avserver.info:8000/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/](http://linuxblog.avserver.info:8000/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/)

I still get the problem. The problem is more noticeable when I use youtube or stream radio. Anything that uses a high amount of bandwidth...

Not sure if it is just specific to a type of driver/system. Typing in the terminal:
> *lshw -C network*
Returns:
description: Wireless interface
product: Centrino Wireless-N 1030

The compuer I am on is a HP Pavilion dm4.


I hope a solution can be found soon.

---

### Post by anuvnu387 on 2013-04-05
Just correcting the URL posted by yocta as it may help others: [http://linuxplained.com/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/](http://linuxplained.com/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/)

---

