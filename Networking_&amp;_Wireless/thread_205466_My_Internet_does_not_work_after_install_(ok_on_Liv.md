---
title: "My Internet does not work after install (ok on LiveCD)"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by chris9902 on 2006-06-28
My internet connection does not work when I install Ubuntu but is ok if I use the LiveCD.

I've read the help guide but it points me to links on the net so I'm stuck in a loop.

I have a Linksys WAG354G router and it works like I say on the LiveCD before install but not after.

can anyone help

---

### Post by Highlag on 2006-06-28
Try disabling and enabling your ethernet card.

You will find it under:
System/Administration/Network

---

### Post by sayanchak on 2006-06-28
On most laptops, including mine, the Ethernet is on eth0, the wireless is on eth1.

At System>Administration>Networking, set Default Gateway to the name of your Wireless card. (Maybe, eth1)

---

