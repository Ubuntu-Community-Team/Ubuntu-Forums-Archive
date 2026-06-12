---
title: "Wired connection not working / Dell D620 help"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by randyrick on 2009-11-18
I'm not currently able to connect through to my wired connection but am able to just fine wirelessly, not sure what happened?  I get a light when the ethernet cable is attached & others can connect through the same cable just fine. When I go through Network Manger to try to edit the eth0 settings & click apply, I can see that it tries to negotiate a connection but after some time just fails.

lspci:
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

interfaces;
auto lo
iface lo inet loopback

dhclient eth0;
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:15:c5:50:c7:86
Sending on   LPF/eth0/00:15:c5:50:c7:86
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



I'm on a Dell D620 running the latest Karmic Koala release;
Linux dell-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux


Any help that would get me connected would be appreciated.

---

### Post by eremyja on 2009-11-18
what does ifconfig return?

---

### Post by randyrick on 2009-11-18
> **eremyja said:**
> what does ifconfig return?



eth0      Link encap:Ethernet  HWaddr 00:15:c5:50:c7:86
          inet6 addr: fe80::215:c5ff:fe50:c786/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10265 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:877499 (877.4 KB)  TX bytes:8609 (8.6 KB)
          Interrupt:18

eth1      Link encap:Ethernet  HWaddr 00:16:cf:61:81:ec
          inet addr:10.92.0.127  Bcast:10.92.3.255  Mask:255.255.252.0
          inet6 addr: fe80::216:cfff:fe61:81ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6279 errors:0 dropped:0 overruns:0 frame:19444
          TX packets:7842 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3734614 (3.7 MB)  TX bytes:1109871 (1.1 MB)
          Interrupt:17 Base address:0xc000

eth0:avahi Link encap:Ethernet  HWaddr 00:15:c5:50:c7:86
          inet addr:169.254.9.74  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by eremyja on 2009-11-18
what is eth1? do you have 2 ethernet controllers? and did you set up the 10. network

---

### Post by randyrick on 2009-11-18
> **eremyja said:**
> what is eth1? do you have 2 ethernet controllers? and did you set up the 10. network

eth1 is the wireless connection that works just fine. wirless negotiates  automatically just fine, that's the 10. network. see lspci above, just one ethernet controller.

---

### Post by eremyja on 2009-11-18
what does less etc/network/interfaces return?

---

### Post by randyrick on 2009-11-18
> **eremyja said:**
> what does less etc/network/interfaces return?

As stated in original post;

randy@dell-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

randy@dell-laptop:~$

---

### Post by eremyja on 2009-11-18
oops totally missed that part :oops:

add this to the end of that
```
auto eth0
iface eth0 inet dhcp
```

---

### Post by randyrick on 2009-11-18
Here's the output after I edit & restart networking;

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:15:c5:50:c7:86
Sending on   LPF/eth0/00:15:c5:50:c7:86
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:15:c5:50:c7:86
Sending on   LPF/eth0/00:15:c5:50:c7:86
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
^[[A^[[A^[[A^[[A^[[A^[[ADHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by sandman42 on 2009-11-18
> **eremyja said:**
> ```

iface eth0 inet dhcp
```

Are you sure you have a DHCP and it's working correctly?
Are you able to set up a static address??
What happens if you do?

BTW, in case you need it, this is a working config:

```
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameserver 151.99.125.2
auto eth0
```


Ciao

---

### Post by randyrick on 2009-11-20
Looks like I discovered some strange Bug with this latest Kernel version, 2.6.31-14.  When I revert back to previous Kernel, 2.6.28-16, I can connect through the wired network just fine :)

---

### Post by alwyn.schoeman on 2009-12-08
I'm suddenly having similar issues.  Dell 830, Karmic. kernel 2.6.31-15.

Today my wired connections are dropping every few minutes, no idea why.  It gets a DHCP address, I do some work, then it drops and a while later I'm online again.

Nothing in the logs.

---

### Post by xx58 on 2009-12-12
:rolleyes:Same problem and don't know what do too? I read everything just what I find and I try everything. Wired Internet connection dropping and little bit later connects again and about 3 hours drops and don't connect anymore. Then I just turn Router and Computer off and On again and everything works again and EVERYTHING repeats again. Any HELP?

---

