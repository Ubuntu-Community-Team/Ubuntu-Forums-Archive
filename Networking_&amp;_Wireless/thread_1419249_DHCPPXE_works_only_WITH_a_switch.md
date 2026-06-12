---
title: "DHCP/PXE works only WITH a switch?"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by benign on 2010-03-01
I have a windows 2008 domain. I've created an ubuntu clonezilla server on the same network to clone machines that I boot up, so there are two DHCP servers on the network when I power up the clonezilla machine. 

I'm curious to know why clients only get an IP from the clonezilla DHCP server if they have a switched hooked between them and the wall port. If they are hooked directly into the wall port, they won't communicate with the clonezilla DHCP server.

 I've tried this with more than a few types of unmanaged switched (I haven't tried managed). Can someone explain why this behavior comes about? I'm thinking it has something to do with ARP cache on our main switches or something similar.

---

### Post by Stuart42 on 2010-03-01
There is a better way.
I would use [FOG](http://www.fogproject.org/)

Install it, and tell it to leave it's dhcp server off. You'll have to modify your dhcp server to point to the FOG servers TFTP for PXE requests. See their [documentation here](http://www.fogproject.org/wiki/index.php?title=FOGUserGuide&Itemid=51#Modifying_existing_DHCP_server_to_work_with_FOG)

Good luck!

---

