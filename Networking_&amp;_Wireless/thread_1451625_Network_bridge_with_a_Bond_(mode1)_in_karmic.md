---
title: "Network bridge with a Bond (mode1) in karmic"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by Thomy23 on 2010-04-10
Hi Guys


I just have to configure a network bridge on ubuntu (i know how to do this, no problem). But it should have not eth0 as a member but bond0 (which is an active-passive setup for eth0 and eth1). Can somebody tell me how this works (this might sound strange, but as soon as i configured this in my /etc/network/interfaces i always get a kernel oops on the next restart.

Does anybody of you did this before without problems (i want to use UEC/Eucalyptus and my NCs should have a network bond for redundandcy reasons).


Greets Thomas

---

### Post by Thomy23 on 2010-04-11
*bump* has nobody an idea?

---

### Post by Crafty Kisses on 2010-04-11
Can I see your routing table?
```
route
```

---

### Post by Iowan on 2010-04-11
There are a couple of help pages - dunno if either one applies, or if they help:
[https://help.ubuntu.com/community/OpenVPN]("https://help.ubuntu.com/community/OpenVPN")
[https://help.ubuntu.com/community/UbuntuBonding]("https://help.ubuntu.com/community/UbuntuBonding")

---

