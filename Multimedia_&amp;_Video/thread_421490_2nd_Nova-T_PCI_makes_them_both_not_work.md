---
title: "2nd Nova-T PCI makes them both not work?"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by tek2k on 2007-04-24
I installed Feisty server edition from scratch and used modprobe cx88-dvb to get my Hauppauge Nova-T pci card working. Scanning and receiving signals had no problem at all everything working nicely.

I then added a 2nd card exactly the same as I want to stream from a second multiplex and the system refuses to acknowledge either of the cards. If there is someone out there with 2 or more of these cards running on Feisty please let me know if it works straight off or is there some configuration I need to do? The motherboard only has 2 pci slots  on it. 

If someone can help me with debugging this I would appreciate it as im not sure what I should be looking for.

Thanks.

---

### Post by davmac on 2007-04-24
Hi,

If you have a look at [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) you'll see details of a setup with two Nova-Ts.

If you type, the following, what output do you get?

> modprobe -r -v cx88-dvb
modprobe -v cx88-dvb
dmesg

Dave MacLeod

---

### Post by tek2k on 2007-04-25
Thank you dave.

Using "modprobe -v cx88-dvb" works like a charm.

---

