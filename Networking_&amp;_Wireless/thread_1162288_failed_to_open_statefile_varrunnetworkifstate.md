---
title: "failed to open statefile /var/run/network/ifstate"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by JeffreyRatcliffe on 2009-05-17
On booting my freshly upgrade Jaunty (from Intrepid) machine, I get no networks at all.

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
ifdown: failed to open statefile /var/run/network/ifstate: No such file or directory
ifup: failed to open statefile /var/run/network/ifstate: No such file or directory

If I mkdir /var/run/network/, then I get my network - for this boot, and have the same problem again the next time I boot.

I've reported this ([https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/377432](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/377432)) but I'd love to know if anybody has any ideas here.

It doesn't seem to be a kernel problem, as I also see this with the 2.6.27 kernel that I was successfully using with Intrepid.

---

### Post by rheimbuch on 2009-05-18
I had this problem on an OpenVZ vm running 9.04. In previous versions the creation of /var/run/network/ was handled by /etc/init.d/loopback. In 9.04 this is handled by udev in /lib/udev/rules.d/85-ifupdown.rules. 

So first you need to make sure that udev is running/starting properly. If you're running in something like OpenVZ then udev is disabled and you'll need this fix: [http://www.fs3.ph/article/ubuntu-904-in-an-openvz-ve](http://www.fs3.ph/article/ubuntu-904-in-an-openvz-ve).

---

### Post by JeffreyRatcliffe on 2009-05-18
Thanks for the help.

My problem turned out to be that as I had a /etc/udev/rules.d/85-ifupdown.rules, to fix problems Intrepid was having talking to my Freerunner, /lib/udev/rules.d/85-ifupdown.rules was not being used.

Deleting /etc/udev/rules.d/85-ifupdown.rules fixed things.

---

