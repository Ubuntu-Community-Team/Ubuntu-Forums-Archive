---
title: "using two network cards please help"
date: 2005-03-02
forum: Networking &amp; Wireless
---

### Post by monkeymartin on 2005-03-02
I have a Asus A7N8X delux mother board.  This motherboard has two network cards built in. 

eth0 nforce
eth1 3com

When I installed Ubuntu I was asked which one I would like to be default.  I went with the nforce but know I want to change it to the 3com.  what config files deal with networking. 

when I go to computer  system configuration networking and activate eth1 networking will stay ok on boot but nothing seems to work can't ping [www.google.com](www.google.com) and no web pages will come up

how do I use to network cars with ubuntu

thanks

---

### Post by alastair on 2005-03-02
Well, the interfaces are configured in the file :

/etc/network/interfaces

see : man interfaces

There is a "hwaddress class address" option in here - that /might/ help assigning the correct ethN device.

But which device becomes eth0 and which eth1 is, I think, a question of module load order. So this might be an issue (test after looking at the interfaces file).

There are ways round this though (ifrename, perhaps).

ifconfig -a

Will show the current interface assignments.

---

