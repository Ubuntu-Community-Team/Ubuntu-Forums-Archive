---
title: "Getting Dynamic ip addresses for multiple interfaces how to?"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by sai438 on 2010-05-06
Hi,

I have 4 Ethernet Interfaces.
I need Dynamic IP-Addresses for 2 Interfaces. Can anybody help me how can i achieve that

Thanks,
sairam

---

### Post by myk.dinis on 2010-05-06
Edit the connections for automatic under the ipv4 tab that you want as dynamic...

The other two edit the connections for manual...

Walkthrough:

Right click on the network icon in your top panel
Select Edit Connections
Select the interface (eth0, eth1, etc...) and click edit
Go to the ipv4 tab and change automatic to manual and edit the address settings (this is for the static interface, reverse the directions for automatic)
Hope this helps!

-myk

---

### Post by Iowan on 2010-05-06
Having more than one interface in the same subnet breaks some networking rule (which I can't quote) - it plays havoc with routing, although some custom **iptables** rules might make it work.
[This]("http://ubuntuforums.org/showthread.php?t=1001843") thread might suggest otherwise...

---

### Post by sai438 on 2010-05-07
Thanks for your reply Myk, Iowan

Its completely different subnets. 
If u do a dhclient on one interface when other interface has already a dynamic IP-Address, it is throwing an error saying already dhclient is running.

whether any configuration that i need to do for getting multiple dhclient processes?

Thanks,
sairam

---

