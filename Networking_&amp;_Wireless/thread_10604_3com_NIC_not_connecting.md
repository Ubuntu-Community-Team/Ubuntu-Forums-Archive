---
title: "3com NIC not connecting"
date: 2005-01-09
forum: Networking &amp; Wireless
---

### Post by cmoir on 2005-01-09
Ubuntu installed fine, however I can't connect to the LAN, even though I'm using a common 3Com Ethernet card. What's more Windows and Suse Linux 9.1 which I tried previously worked fine on the same machine.

I think the problem might be that the network card (3Com 3c900) has 2 interfaces, a 10base2 coax BNC connector as well as a more usual 10baseT. I'm using the BNC connector.

Windows works fine, and I managed to get the Suse Linux drivers to work by altering a config file to force the card to use the BNC connector.

There are open source drivers here: [http://www.scyld.com/vortex.html](http://www.scyld.com/vortex.html) which imply that these drivers can be set to be auto-select. I have no idea if these are the divers that Ubuntu uses or whether it uses 3C ones. How do I find out?

Where is the network card configured? Is there a config file somewhere that I can mess with to force it to select 10base2 interface?

Any help much appreciated.

---

### Post by randy on 2005-01-10
Ubuntu probably puts the config file in a similiar place as Suse did.  Where was the file that you needed to edit under Suse?

---

### Post by az on 2005-01-10
/etc/network/interfaces

---

### Post by ynef on 2005-01-10
Please post the output that "sudo lspci" and "sudo lsmod" give you. The first tells us what PCI devices Linux finds, the second tells us what modules you've got loaded at the moment.

While you're at it, post the output of "ifconfig" too.

If you've got eth0 in the ifconfig, the module is loaded and ready, and you just have to set your interface up correctly. We can help with that, and so can google.

---

