---
title: "AVM Fritz! Card pci 2.0"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by Lorenzot on 2006-06-04
I have an *AVM Fritz! Card PCI 2.0* (isdn) on Ubuntu 5.10.
I was read the ISDNHowTo here: [https://wiki.ubuntu.com/IsdnHowto]("https://wiki.ubuntu.com/IsdnHowto")

> PCI

1. create /etc/hotplug/backlist.d/isdn with:

- hisax
- hisax_fcpcipnp

2. reboot so that the avm/capi modules get loaded

3. Create the connection with "Desktop/Adminstration/Networking"

4. pon ppp0; poff should work now

(sucessfully tested with AVM fritz card A1 (2.0))

When I write 'pon ppp0', the output is:

> plugin userpass.so loaded.
userpass: $revision: 1.5 $
plugin capiplugin.so loaded.
capiplugin: $revision: 1.36 $
capiconn: 1.13

but I can't surf on the net.

p.s. sorry my HORRIBLE english... I am italian :-| . But in the Ubuntu's italian forum no one can help me.

---

### Post by Lorenzot on 2006-06-04
.

---

