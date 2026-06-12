---
title: "Stopped connecting to wireless"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by gdana on 2010-11-24
Hello, 

I have a Dell Studio 15 laptop, dual boot with Ubuntu 10.04 and Windows 7. Since installation everything worked seamlessly including the wireless connection. A couple of weeks ago the computer was used with windows 7 for a few sessions and crashed several times due to some problematic software. Since then, the Ubuntu wireless connection stopped working, it tries to connect but never succeeds. On windows the wireless connection still works properly.

[I]lspci:
[/I] 
Network Controller: Intel Corporation Wireless WiFi Link 5100
Ethernet Controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe

*ifconfig:*

wlan0 Link encap:Ethernet HWaddr (...)
inet6 addr: fe80:...:/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes: 2036 (2.0 KB)

Not sure how it was before exactly, but I do know that wlan0 had a static IP address next to it, and that it was accessible from other computers on the network.

Any help would be most appreciated...

---

### Post by grahammechanical on 2010-11-24
From your listing wlan0 is UP and RUNNING but it does not show a network address. You should be showing an Internet address ( inet addr: ) of the modem/router. Here ia a link to the trouble shooting guide.

[https://help.ubuntu.com/community/WifiDocs/](https://help.ubuntu.com/community/WifiDocs/)

Regards.

---

### Post by pawhtiobo on 2010-11-24
What configuration do you have in:

/etc/network/interfaces



See ya....

---

### Post by gdana on 2010-11-24
/etc/network/interfaces:

auto lo
iface lo inet loopback

---

### Post by pawhtiobo on 2010-11-24
Hi :)

Some things are missing in the /etc/network/interfaces, here is my config:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

#The wireless interface
auto wlan0
iface wlan0 inet dhcp
wireless-mode Managed
wireless-essid **yourssid**
wireless-key s:**mywpakey**

Is your Wlan card detected in the system, when you run the command lspci?

Are you using Gnome network manager?

See ya

---

### Post by bkratz on 2010-11-24
> **pawhtiobo said:**
> Hi :)

Some things are missing in the /etc/network/interfaces, here is my config:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0

iface eth0 inet dhcp

#The wireless interface
auto wlan0
iface wlan0 inet dhcp
wireless-mode Managed
wireless-essid **yourssid**
wireless-key s:**mywpakey**

Is your Wlan card detected in the system, when you run the command lspci?

Are you using Gnome network manager?

See ya

This is what is in mine. If you are using network manager ( and did not set it up manually) it is correct.


```
auto lo
iface lo inet loopback

```

---

