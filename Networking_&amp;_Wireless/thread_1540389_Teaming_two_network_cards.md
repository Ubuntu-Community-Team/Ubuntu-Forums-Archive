---
title: "Teaming two network cards"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by Xi0N on 2010-07-27
Im setting up a server that has two network cards.

When im installing im given the choice to use either eth0 or eth1... and from then on, i only see the one i choose.

Can i merge both nics in one same interface, and still have one single ip?
Is this safe for using such interace with virtualbox?

Do you have some detailed how-to on how to configure this?

Thanks!!!!!

---

### Post by gombadi on 2010-07-27
It is called bonding -

[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding) and other sites around the Internet.

The type of bonding depends on how your network is configured and what you want i.e. fail-over v extra bandwidth.

Virtualbox should be fine with a bond0 interface.

---

