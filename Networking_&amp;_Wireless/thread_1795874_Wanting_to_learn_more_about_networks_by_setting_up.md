---
title: "Wanting to learn more about networks by setting up my own."
date: 2011-07-03
forum: Networking &amp; Wireless
---

### Post by perrti-y02 on 2011-07-03
Hello,

As the title suggests I am looking into building a small network in my home. I am aware that what I want to do can easily be done using a router but it is my intention to build the entire thing from the ground up.

I want to create a full network that has wireless and wired functionality and can connect 2 laptops (wireless) a desktop, a file server and an xbox (possibly wireless).

As I understand it, to do this (without using a router) I would need an ADSL modem, a small and low powered machine to act as a firewall, DHCP server and for port forwarding (I want the fileserver to be visible to the internet, but securely) a switch and a wireless bridge.

Essentially I want to know if this is correct. Is there a better way to do this? Have I missed anything?

Many Thanks

Tim Perrin.

---

### Post by helgman on 2011-07-03
> **perrti-y02 said:**
> As I understand it, to do this (without using a router) I would need an ADSL modem, a small and low powered machine to act as a firewall, DHCP server and for port forwarding (I want the fileserver to be visible to the internet, but securely) a switch and a wireless bridge.

That should pretty much do it.

If you want to go "all in" you might be able to work around the wireless bridge by installing a wireless NIC in one of the permanent machines on the network (the "low powered" or the desktop) and then bridge that NIC to the wired NIC, extending the wired network ([https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)).

Or you could build two "subnets" (one wired and one wireless) and use the "low powered" machine (router) to move traffic between the two (if you have two wired and one wireless NIC installed in it).

Good luck!

Regards,
Helgman

---

### Post by Drenriza on 2011-07-03
> **perrti-y02 said:**
> Hello,

As the title suggests I am looking into building a small network in my home. I am aware that what I want to do can easily be done using a router but it is my intention to build the entire thing from the ground up.

I want to create a full network that has wireless and wired functionality and can connect 2 laptops (wireless) a desktop, a file server and an xbox (possibly wireless).

As I understand it, to do this (without using a router) I would need an ADSL modem, a small and low powered machine to act as a firewall, DHCP server and for port forwarding (I want the fileserver to be visible to the internet, but securely) a switch and a wireless bridge.

Essentially I want to know if this is correct. Is there a better way to do this? Have I missed anything?

Many Thanks

Tim Perrin.

why not use a cisco router for your home network. Why "build" a router?

---

### Post by perrti-y02 on 2011-07-03
The reason I want to 'build' a router is to learn what is going on with a network. I want to learn how to set up a DHCP server, port forwarding, serving and I want to see it at work. I know it is not the simplest way to do it or the quickest, or the best but it will teach me.

---

