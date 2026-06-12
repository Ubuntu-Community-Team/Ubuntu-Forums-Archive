---
title: "No network after upgrade to 12.04"
date: 2012-10-14
forum: Networking &amp; Wireless
---

### Post by Impavidus on 2012-10-14
After upgrading my older computer from 10.04 LTS to 12.04 LTS the (wired) network connection stopped operating. When booting, the computer waits about two minutes with the notification 'Waiting for network configuration...', then completes booting without network connection. After logging in I can easily start the connection by issuing the command 'sudo service network-manager start'. Off course, this is inconvenient, not in the least because not all users have root privileges. It sounds like some error in some boot script, probably having something to do with network-manager.

I already tried 'sudo apt-get --reinstall install network-manager', but without effect.
I am using the xfce desktop, but I don't think it has anything to do with it.

---

### Post by Finnicella on 2012-10-14
Hi,
check the "interfaces" file with:
```
cat /etc/network/interfaces
```
Bye

---

### Post by firekage on 2012-10-14
I had the same problem with going from 11.10 to 12.04. In my case i have to manually edit interfaces:

> 
firekage@deusex:/etc/network$ cat interfaces 
# the loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

# The secondary network interface
auto eth1
iface eth1 inet dhcp
and edit manually /etc/NetworkManager/NetworkManager.conf

> firekage@deusex:/etc/NetworkManager$ cat NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
**managed=true**
firekage@deusex:/etc/NetworkManager$ 

After this restart ubuntu or service.

---

### Post by Impavidus on 2012-10-21
I looked in it again this weekend  and by comparing to the /etc/network/interfaces file on my laptop I solved it. I commented out every line in /etc/network/interfaces exept those concerning the loopback device and it worked. I have still no idea why.

Anyway, thanks for pointing me to the interfaces file.

---

