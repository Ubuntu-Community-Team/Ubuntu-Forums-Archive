---
title: "Intel e1000e nic seen as em0 instead of eth0"
date: 2013-05-17
forum: Networking &amp; Wireless
---

### Post by eclay on 2013-05-17
I've just installed Ubuntu 13.04 on a system with a Intel 82574L e1000e nic.  When I went to check the output of ifconfig I get the following.

em0       Link encap:Ethernet  HWaddr 00:22:4d:7a:94:5f  
          inet addr:10.10.0.66  Bcast:10.10.0.255  Mask:255.255.255.0

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0

When I check dmesg I see both eth0 and em0 entries.

Does anyone know why the interface name has changed to em0 instead of eth0?

---

### Post by praseodym on 2013-05-17
Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsmod
cat /etc/network/interfaces
cat /etc/udev/rules.d/70-persistent-net.rules
ifconfig -a
```

---

### Post by eclay on 2013-05-17
As requested


lspci -nnk|grep -iA2 net
01:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]
    Subsystem: Intel Corporation Device [8086:2011]
    Kernel driver in use: e1000e

Module                  Size  Used by
vesafb                 13828  0 
coretemp               13355  0 
microcode              22881  0 
psmouse                95870  0 
serio_raw              13215  0 
joydev                 17377  0 
lpc_ich                17061  0 
gma500_gfx            192624  1 
video                  19390  1 gma500_gfx
drm_kms_helper         49394  1 gma500_gfx
drm                   286313  2 drm_kms_helper,gma500_gfx
mac_hid                13205  0 
i2c_algo_bit           13413  1 gma500_gfx
lp                     17759  0 
parport                46345  1 lp
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
ahci                   25731  2 
libahci                31364  1 ahci
e1000e                198787  0 

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto em0
iface em0 inet dhcp


# ifconfig -a
em0       Link encap:Ethernet  HWaddr 00:22:4d:7a:94:5f  
          inet addr:10.10.0.66  Bcast:10.10.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:4dff:fe7a:945f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4945 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4561759 (4.5 MB)  TX bytes:886946 (886.9 KB)
          Interrupt:16 Memory:d0020000-d0040000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)


the /etc/udev/rules.d/70-persistent-net.rules is empty

---

### Post by praseodym on 2013-05-17
Remove anything except
```

auto lo
iface lo inet loopback
```
from the interfaces-file and reboot.

---

### Post by eclay on 2013-05-17
Thanks for your reply.  when I removed the em0 lines from /etc/network/interfaces and then rebooted the system rebooted with no eth0/em0 IP.  When I tried to then add eth0 to the /etc/network/interfaces file and bring the interface up it said no interface could be found.  Ifconfig -a shows lo and em0.  So I changed eth0 to em0 and brought the interface online and I'm again able to access this system.

Does anyone know why the name change in ubuntu 13.04 for intel e1000e interfaces?

---

### Post by eclay on 2013-05-17
Ah "light bulb".  I had to add a line to the /etc/udev/rules.d/70-persistent-net.rules file to specify that eth0 should have the logical name of eth0 instead of em0.

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:4d:7a:94:5f", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

This page was helpful also:
[http://bit.ly/11L8oHX](http://bit.ly/11L8oHX)

---

