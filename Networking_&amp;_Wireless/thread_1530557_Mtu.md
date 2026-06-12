---
title: "Mtu"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by Scott Swinyard on 2010-07-13
What is the default Mtu in 10.04 and how do I set it permanently?

---

### Post by Iowan on 2010-07-13
My machine is set for **MTU: automatic **in Network Manager.  **ifconfig** shows the interface with MTU:1500.

---

### Post by Scott Swinyard on 2010-07-14
I hate to bump this up just to do this, but I need to say thanks for the info.

Thanks.

---

### Post by bkratz on 2010-07-14
I may be doing something wrong, but I right clicked on the network icon went to edit connections--selected either wired or wireless-- highlighted it and selected edit. The first tab shows the current MTU setting. I then simply used the arrow keys to select 1492 which has always worked a little better than the default 1500 ( your mileage may vary!) and it seems to stay there permanently.

---

### Post by dragin33 on 2010-07-15
Bumping the MTU may give you a speed increase in large file transfers but will slow down regular internet traffic and high latency apps like games.

Source: [http://www.asicdesigners.com/jumbo_enet_frames.html](http://www.asicdesigners.com/jumbo_enet_frames.html)


.. But if you're still interested I believe you have to do it on the command line by editing the network card configuration file and adding an MTU line.

---

