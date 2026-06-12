---
title: "Making ethernet static ip automatically"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by tenmilez on 2009-02-20
No matter what I try whenever I restart my computer the ethernet connection resets to eth0 with default settings. What I want is to have it default to a static ip configuration.

---

### Post by ddnev45 on 2009-02-20
I had to edit the /etc/network/interfaces file by hand (as root).

You can do:

```
man interfaces
```

in a teminal for all the details; I attached the examples that can be found in: /usr/share/doc/ifupdown/examples/network-interfaces.

The example:

```
# An example ethernet card setup: (broadcast and gateway are optional)
#
# auto eth0
# [COLOR="Blue"]iface eth0 inet static[/COLOR]
#     address 192.168.0.42
#     network 192.168.0.0
#     netmask 255.255.255.0
#     broadcast 192.168.0.255
#     gateway 192.168.0.1
```

sets up eth0 for a static ip (remember to remove the #'s in your actual file).

---

### Post by Iowan on 2009-02-21
Try [this]("http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html") one.  Another [option]("http://ubuntuforums.org/showpost.php?p=6774735&postcount=3") is to un-install Network Manager, and re-install the older version.

---

### Post by lensman3 on 2009-02-21
I had to uninstall NetworkManager so that it didn't install and run at ALL the run-levels.  Then I had to hook up the network script and have it installed at run-level 2,3 & 5.  NetworkManager doesn't work at all for static IPs.  

The gui interface also had trouble setting the network mask.  It set mine to 255.255.255.255, which won't and didn't work.  I had to hand edit the file in /etc/system/network_interface to 255.255.255.0.

I had to do the above for a dual Ethernet Linux firewall for both interfaces.  I setup the Internet side Ethernet card to use "network" and to get a DHCP address from my providers servers.

Hope this helps.  The NetworkManager is not ready for prime time.  It needs a static option.

---

### Post by lynnevan on 2009-02-21
> **tenmilez said:**
> No matter what I try whenever I restart my computer the ethernet connection resets to eth0 with default settings. What I want is to have it default to a static ip configuration.


**You not the only one w/ this problem.  Maybe some clues here?**  

[http://ubuntuforums.org/showthread.php?t=1076221&highlight=kill+dhcp](http://ubuntuforums.org/showthread.php?t=1076221&highlight=kill+dhcp)

lynnevan

---

