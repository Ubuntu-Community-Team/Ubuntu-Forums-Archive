---
title: "FreeNAS authorized networks"
date: 2013-07-11
forum: Networking &amp; Wireless
---

### Post by feardotcom on 2013-07-11
Ok, so i got a lot of questions about freenas and i cant seem to find straight answers on google.

1) i want to set up a static ip on the freenas. in the start up of freenas i'm assuming thats option 5, Configure Static Routes. It ask for destination network and the gateway IP address. Is the destination network suppose to be the intended ip i want to give it, say for example 192.168.1.60? and the gateway is the default gateway, e.g. 255.255.255.0?

2) When setting up an NFS share, what is Authorized networks? Is that suppose to be for the default gateway as well? So it would be 255.255.255.0?

3) In the authorized IP address is there a way to span it across multiple ip's without having to type them in one at a time, for example, i want to be able to see ip's from 100-149, so would i do 192.168.1.100/50?

4)What do i need to do on the client end to see the share? Because i have been messing with it and i cant see anything. and yes the nfs service is on.

Please help.

---

### Post by feardotcom on 2013-07-11
I got samba to work, but all the pcs in the house are linux and so i dont really want to go around to 6 pc's and install samba and set it up.

---

### Post by tgalati4 on 2013-07-11
Depending on your version of freenas, you set up static networking under the tab Network-->Lan Management

Set up static IP, for example 192.168.1.162/24  (I presume that 24 is the network mask:  255.255.255.0)
Set up gateway IP, for example 192.168.1.1  (address of your router, typically)

Static routes are used to specify how to get to another specific network from your network--normally only needed in a corporate environment with many, many networks.

---

### Post by feardotcom on 2013-07-12
ok thank you, do you have any info on nfs?

---

### Post by feardotcom on 2013-07-13
bump

---

### Post by varunendra on 2013-07-13
Hello feardotcom,

Not to invalidate your questions, but -
> **feardotcom said:**
> Ok, so i got a lot of questions about freenas and i cant seem to find straight answers on google........
None of your questions are Ubuntu specific. Even the last one is a general question to which you'll get good enough help on FreeNAS support pages/forums. Also -
> **feardotcom said:**
> i dont really want to go around to 6 pc's and install samba and set it up.
Another reason why you should look into the native solutions in FreeNAS which are pretty straight forward as far as I know.

Therefore, I believe you'll get much better help on the community support pages of FreeNAS : [http://www.freenas.org/get-help.html#community](http://www.freenas.org/get-help.html#community)
and its community forums : [http://forums.freenas.org/](http://forums.freenas.org/)

Personally, unless you want a complex sharing policy and/or mounting shares at boot time (in clients), I think you shouldn't need to configure absolutely anything in the clients.

---

### Post by tgalati4 on 2013-07-16
Once your network settings are correct in freenas, the network shares should show up automatically on other computers without making any changes to the client machines.

---

