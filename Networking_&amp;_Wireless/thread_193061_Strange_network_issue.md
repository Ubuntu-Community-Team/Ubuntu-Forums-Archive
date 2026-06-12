---
title: "Strange network issue"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by mbower on 2006-06-09
I have searched through the forums here and did some google searching, so I apologise in advance if this is already a topic.

I am running 6.06 server and I have a static IP set.  Twice now it seems like the network service restarts and when I check to see why I can't access it, it has an IP assigned from the DHCP server.  So, I restart the networking service ```
sudo /etc/init.d/networking restart 
``` and it is fixed with the correct static IP that I have set in the /etc/network/interfaces file.  

  ```
 This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 10.91.92.120
        netmask 255.255.252.0
        broadcast 10.91.92.255
        gateway 10.91.92.1

```

any thoughts?

---

### Post by bswilson on 2006-06-09
What is the purpose of the **broadcast** statment in your **interfaces** file?  I wonder if removing that would make any difference?

---

### Post by mbower on 2006-06-11
[QUOTE=bswilson]What is the purpose of the **broadcast** statment in your **interfaces** file?  I wonder if removing that would make any difference?[/QUOTE]

Far as I know, it just broadcasts to the other network devices.

---

