---
title: "How to maintain static IP address"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by rick_woodham on 2009-04-04
I am using Ubuntu 8.10 and it recognizes my ethernet connection without any problem using the Auto Eth0 setting.  However, I am using this box as a server and want to maintain a static IP address on my network.  I have configured as a static IP and the connection changes apply and function without any problems.  However, when I reboot, the Auto Eth0 comes back to life using DHCP (which it gets from my Smoothwall firewall).  No matter what I try, it seems that I can only maintain a static IP until the next reboot.  Any suggestions on how to make this a permanent change?

---

### Post by Iowan on 2009-04-04
Consider a static lease (if the Smoothwall machine is capable) - the DHCP server issues the same IP Address based on MAC address.

---

### Post by CyberMando on 2009-04-04
auto eth0 tells ifup to configure the interface at boot. The line 
iface eth0 inet dhcp
tells it to do DHCP.Did you change that to
iface eth0 inet static 
and then add the rest of the info?

Do you have network-manager installed? If so does /etc/NetworkManager/nm-system-settings.conf have
[ifupdown]
managed=false

---

### Post by rick_woodham on 2009-04-04
The expression can't see for the forest for the trees comes to mind.  Actually, using my Smoothwall firewall to issue the static IP address works very well and give me flexibility on the Ubuntu server in the event I need to move it.  I'll file away the required Ubuntu network changes to accomplish the same result, but for now, the firewall solution works great.  Thanks for the support.

---

