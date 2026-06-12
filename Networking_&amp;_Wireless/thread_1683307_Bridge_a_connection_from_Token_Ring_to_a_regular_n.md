---
title: "Bridge a connection from Token Ring to a regular network card?"
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by chmcke01 on 2011-02-07
My brother goes to a school where they used to have token ring internet, then they upgraded the regular dorms to Ethernet but then ran out of money so didn't upgrade the family housing (where he lives with his wife and 3 kids). So, the only internet available to him is token ring. He has a desktop set to dual boot with Windows Vista and Ubuntu.

I told him he should install the Token Ring network adapter and keep the regular network card installed as well. Then bridge the two connections. Then, he could run a cable from his network card to a wireless router and that should fix his internet issues.

But I don't know if there are drivers for token ring adapters or how to bridge the connections in Ubuntu if we find them. If it will work he will buy a Token Ring adapter. If you were in his setup how would you resolve your lack of internet?

---

### Post by chmcke01 on 2011-02-08
Nobody knows how to help me?

---

### Post by mips on 2011-02-08
What is the make & model of the Token Ring adapter so we can check linux compatibility. We can take it further after that.

---

### Post by chmcke01 on 2011-02-08
> **mips said:**
> What is the make & model of the Token Ring adapter so we can check linux compatibility. We can take it further after that.

My brother is going to try to find it, but it came in a generic unmarked box.

---

### Post by mips on 2011-02-08
> **chmcke01 said:**
> My brother is going to try to find it, but it came in a generic unmarked box.

Well the card or the chips on it should still be marked. Maybe a clear digital photo of it would be better.

---

### Post by oldfred on 2011-02-08
I have not used token-ring for 15 years. But I did bridge it with Novell.

These are the drivers still in Ubuntu:

fred@fred-LT-A105:~$ find /lib/modules | grep token
/lib/modules/2.6.35-24-generic/kernel/drivers/net/tokenring
/lib/modules/2.6.35-24-generic/kernel/drivers/net/tokenring/tmspci.ko
/lib/modules/2.6.35-24-generic/kernel/drivers/net/tokenring/3c359.ko
/lib/modules/2.6.35-24-generic/kernel/drivers/net/tokenring/abyss.ko
/lib/modules/2.6.35-24-generic/kernel/drivers/net/tokenring/olympic.ko
/lib/modules/2.6.35-24-generic/kernel/drivers/net/tokenring/tms380tr.ko

---

### Post by chmcke01 on 2011-02-08
> **mips said:**
> Well the card or the chips on it should still be marked. Maybe a clear digital photo of it would be better.

Its an IBM 16/4 Token Ring PCI Adapter 2. I will see about getting a picture.

---

### Post by mips on 2011-02-09
> **oldfred said:**
> I have not used token-ring for 15 years. But I did bridge it with Novell.

These are the drivers still in Ubuntu:

fred@fred-LT-A105:~$ find /lib/modules | grep token
/lib/modules/2.6.35-24-generic/kernel/drivers/net/tokenring
/lib/modules/2.6.35-24-generic/kernel/drivers/net/tokenring/tmspci.ko
/lib/modules/2.6.35-24-generic/kernel/drivers/net/tokenring/3c359.ko
/lib/modules/2.6.35-24-generic/kernel/drivers/net/tokenring/abyss.ko
**/lib/modules/2.6.35-24-generic/kernel/drivers/net/tokenring/olympic.ko**
/lib/modules/2.6.35-24-generic/kernel/drivers/net/tokenring/tms380tr.ko

Thanks!

You sure you bridged it and did not route it as you can generally not bridge between different network topologies seeing the addressing and frame sizes are different? That is unless your equipment supports translational bridging like Cisco does. I could be wrong though and will do a bit of research.

Edit: I did a bit of searching and it looks like this was possible on older versions of Netware but not the newer ones.


> **chmcke01 said:**
> Its an IBM 16/4 Token Ring PCI Adapter 2. I will see about getting a picture.

That card will work with the Olympic driver as listed by oldfred above so you are good to go, don't worry about a picture ;)

Confirmation,
[http://www.linuxtr.net/documentation/howtohtml/drivers.html#IBMTR](http://www.linuxtr.net/documentation/howtohtml/drivers.html#IBMTR)
[http://tldp.org/HOWTO/Hardware-HOWTO/nic.html](http://tldp.org/HOWTO/Hardware-HOWTO/nic.html)

You cannot bridge between Token Ring & Ethernet (well in Linux anyway as far as I know) but you will be able to route between them which will still solve your problem!

Routing will work the same way as for between two ethernet interfaces.

---

### Post by chmcke01 on 2011-02-10
According to him, when my brother tries to install the card it just looks for the driver online and won't let him search his system for it. However, he's not online yet so it can't find it online either. How does he tell the system to use the Olympic driver?

---

### Post by mips on 2011-02-10
> **chmcke01 said:**
> According to him, when my brother tries to install the card it just looks for the driver online and won't let him search his system for it. However, he's not online yet so it can't find it online either. How does he tell the system to use the Olympic driver?

Well it's a kernel module so it should pick it up.

Does linux detect the card, can check with **lspci -v**
Has he tried adding the module with modprobe?

This might be the long way around but a reinstall with the card could solve the problem. Sorry I'm not of anymore use.

---

### Post by chmcke01 on 2011-02-19
The computer picks up the network card (but it says unknown device tr0) but when he plugs it into the wall it doesn't pick up an IP address. What does he need to try next?

---

### Post by SamusAran on 2012-07-17
This is an interesting forum. Token Ring isnt widely used, but its good to know that you can do this in Linux. I would suggest setting up a dhcp server and shorewall firewall in ubuntu. I turned my ubuntu install into a router by installing dhcp, shorewall, and a few other services. there should be some how to guides online although granted the documentation can be spotty. But this is a project and it will take some learning. Basically, your brother will not use a router, except for wireless. and this also presents a problem because if your brother boots into windows, his internet goes down. his best bet is to buy a second computer and set it up as a dedicated linux router to route the traffic between token ring and ethernet. or to buy an out of the box router(maybe from cisco, or ibm) that will route between token ring and ethernet. I know there are a few out there. Try checking on ebay for a router. post your results, and good luck!

---

### Post by wildmanne39 on 2012-07-17
Hi, this is an old thread so it has been closed, thanks for sharing.

---

