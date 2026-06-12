---
title: "Remote Wake on Lan"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by Dsky on 2010-12-18
There's any program like this for ubuntu?

[IMG]http://www.dreamsworld.it/emanuele/wp-content/uploads/2007/04/2007-04-12_wakeonlan.jpg[/IMG]


edit: there is wakeonlan :D, but what have i to do if i want to wake the pc on WAN?

---

### Post by Dsky on 2010-12-19
up

---

### Post by iponeverything on 2010-12-19
WOL is OSI layer 2.

So no, no Wake on WAN.

---

### Post by Dsky on 2010-12-19
ehm... can u explain me better?

---

### Post by iponeverything on 2010-12-19
Setup a border box that can trigger the required magic packet on it's internal interface when told to do so through a WAN accessible webpage or some other mechanism.

---

### Post by tgalati4 on 2010-12-19
WOL is Wake on LAN.  LAN is Local Area Network.  For a remote wake--outside of your LAN, you want Wake on WAN.  There is no such thing.

If you have a machine that is always on, then you can write a script to send WOL internally to wake up another machine on the same network.  

There are some phone-triggered and ethernet-triggered power strips that can wake servers up with a phone call or a ping to an appropriate IP address.  They are expensive.

---

### Post by Dsky on 2010-12-20
my router (netgear dg834g) is always up so if i can acced at the router i could wake up a machine no?

---

### Post by iponeverything on 2010-12-20
if the router will support the dd-wrt firmware -- then yes.

---

