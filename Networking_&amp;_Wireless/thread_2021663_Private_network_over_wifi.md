---
title: "Private network over wifi"
date: 2012-07-09
forum: Networking &amp; Wireless
---

### Post by sombrancelha on 2012-07-09
Hello,

I have two computer which I want to connect on a private network, so I can ssh from one into the other. However, I don't want them to be connected to the internet (if needed, I can connect to the internet during configuration, but they must run autonomously after).

Also, one of the computers does not have a wifi card. Can I connect the it to a wireless router and "share" it through the router?

How do I go about configuring the network?

Thanks

---

### Post by gertvdijk on 2012-07-09
I think what you try to explain is like the following. An isolated network for two computers only, connected via networking hardware you already have (a wireless+wired internet gateway). And with isolated you want it not to be able to connect to other hosts in the network and not being able to use the internet. Is that correct?

Then this is possible by setting a different subnet for the two computers. Most probably your internet gateway device won't let you offer to configure VLANs, so it will be in the same physical LAN. Not very secure, but only secure in terms of 'security by obscurity'. If you really need security for this, you should provide more details about your networking hardware to see if it supports VLANs.

If we continue on a less secured network, you can just configure both PCs to be in a different subnet than the one you regularly use (for internet connected computers). So first find out what the current subnet is and avoid that. For example, if it is now 192.168.1.0/24 (meaning hosts 192.168.1.1 - 254), then you could make up something like 192.168.2.0/24. (/24 is the same as 255.255.255.0, just a different notation). It's possible to configure this yourself in the GUI in your network manager in Ubuntu. Just change the current configuration of your wired network to not do DHCP but set it manually. Make sure both hosts have unique host address (let's say 192.168.2.10 and .11), you configure your broadcast at the end (192.168.2.255) and both use /24 or 255.255.255.0. You can leave out the gateway and DNS fields. Then you should be able to ping each other.

I do assume you don't have isolated wired and wireless in your current Access Point.

Does this help?

---

### Post by sombrancelha on 2012-07-10
Hi gertvdijk,

Thank you for replying so quick and thoroughly. However, I'm afraid that was not my question. Let me try to explain it in other words.

Computer 1 does not have a wireless card. Computer 2 has a wireless card. Computer 1 will be on a robot in the field, so it will not have an internet connection. I want to be able to control Computer 1 with Computer 2 (ssh). Therefore, I need to set up a network between them.

I have a wireless router and I was hoping I could connect it's ethernet port to Computer 1's ethernet port. Does that work? Can I connect the wireless router ethernet port to a computer or do I have to connect it to the internet?

I don't need to set up file and folder sharing, just need to connect both computers to the same network.

---

### Post by sombrancelha on 2012-07-10
Problem solved. Answering my own question: yes, it is possible to connect the wireless router to the ethernet port of a computer.

For future searches: I had to manually configure the IP (static) of the machines in order to get it working. I also had to fiddle with the router's configuration.

---

