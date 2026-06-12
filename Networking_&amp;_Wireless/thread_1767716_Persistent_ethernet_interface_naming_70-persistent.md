---
title: "Persistent ethernet interface naming: 70-persistent-net.rules being ignored"
date: 2011-05-26
forum: Networking &amp; Wireless
---

### Post by asadr on 2011-05-26
I'm running Ubuntu 11.04 on my desktop and the 70-persistent-net.rules file seems to be ignored. The ethernet interfaces are randomly shuffled around on boot (i have 4 interfaces). The original one was configured to have a static IP address (eth0). Is there anything that prevents the /etc/udev/rules.d/70-persistent-net.rules from being applied/used?

```
root@thrall:~# cat /etc/udev/rules.d/70-persistent-net.rules 
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x11ab:0x4320 (skge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:18:f3:1e:01:10", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x148f:0x2070 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="c8:3a:35:cb:2b:18", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x13f0:0x0200 (sundance)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="54:e6:fc:85:bc:f0", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x13f0:0x0200 (sundance)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="54:e6:fc:85:d6:ea", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x13f0:0x0200 (sundance)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="54:e6:fc:85:b5:db", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"

```

After a reboot the names are now:

```
root@thrall:~# ls -al /sys/class/net/
total 0
drwxr-xr-x  2 root root 0 2011-05-26 11:45 .
drwxr-xr-x 46 root root 0 2011-05-26 11:45 ..
lrwxrwxrwx  1 root root 0 2011-05-26 11:45 eth0-eth1 -> ../../devices/pci0000:00/0000:00:1e.0/0000:01:09.0/net/eth0-eth1
lrwxrwxrwx  1 root root 0 2011-05-26 11:45 eth1 -> ../../devices/pci0000:00/0000:00:1e.0/0000:01:0a.0/net/eth1
lrwxrwxrwx  1 root root 0 2011-05-26 11:45 eth2 -> ../../devices/pci0000:00/0000:00:1e.0/0000:01:0b.0/net/eth2
lrwxrwxrwx  1 root root 0 2011-05-26 11:45 eth3 -> ../../devices/pci0000:00/0000:00:1e.0/0000:01:0d.0/net/eth3
lrwxrwxrwx  1 root root 0 2011-05-26 11:45 lo -> ../../devices/virtual/net/lo

root@thrall:~# ifconfig -a
eth1      Link encap:Ethernet  HWaddr 54:e6:fc:85:d6:ea  
          inet6 addr: fe80::56e6:fcff:fe85:d6ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:31
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6275 (6.2 KB)
          Interrupt:21 Base address:0xe400 

eth2      Link encap:Ethernet  HWaddr 54:e6:fc:85:b5:db  
          inet6 addr: fe80::56e6:fcff:fe85:b5db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:12
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6275 (6.2 KB)
          Interrupt:22 Base address:0xe000 

eth3      Link encap:Ethernet  HWaddr 00:18:f3:1e:01:10  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe1e:110/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1117284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1743602 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:126795356 (126.7 MB)  TX bytes:2294837175 (2.2 GB)
          Interrupt:23 

eth0-eth1 Link encap:Ethernet  HWaddr 54:e6:fc:85:bc:f0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1813 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:432200 (432.2 KB)  TX bytes:432200 (432.2 KB)



```

What's odd is that my original /etc/network/interfaces is configured to give eth0 a static IP (or what was originally called eth0) which has a different name on every boot, but somehow still manages to be correctly configured (in the ifconfig output above for eth3 it has a static IP 192.168.1.100):

```
root@thrall:~# cat /etc/network/interfaces
auto lo eth0
iface lo inet loopback

iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1

```

---

### Post by asadr on 2011-06-01
Turns out it was NetworkManager messing everything up after the system configured it correctly. I uninstalled it using:

```
sudo apt-get remove network-manager
```

...and everything works fine now. Damn GUI tools.

---

