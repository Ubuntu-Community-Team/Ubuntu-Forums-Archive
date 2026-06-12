---
title: "WIRED NETWORK disconnected"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by alex18min on 2010-11-20
hi everyone,
i've just bought a new pc HP pavilion DV6 with Windows 7 and i've installed also Ubuntu with a dual boot. 
But i've this problem in Ubuntu: i cannot connect to my wireless router; in fact the wired network doesn't work, and the icon is grey. 
I'm using Ubuntu 9.10.
with the command ifconfig the result is:
eth0     Link encap: Ethernet  HWaddr c8:0a:a9:6f:a8:34
           UP BROADCAST MULTICAST   MTU:1500   METRIC:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:0  (0.0 B)   TX bytes:0  (0.0 B)
           Interrupt:35 Base address: 0xa000

lo        Link encap:Local Loopback
           inet adrr:127.0.0.1   Mask:255.0.0.0
           inet6 addr:  ::1/128 Scope:Host
           UP LOOPBACK RUNNING   MTU:16436  Metric:1
           RX packets:4 errors:0 dropped:0 overruns:0 frame:0
           TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0  txqueuelen:0
           RX bytes:240  (240.0  B)   TX bytes:240  (240.0  B)


please help me!!
Thanks

---

### Post by uncaspi on 2010-11-20
What do you get when you try sudo dhclient eth0

---

### Post by alex18min on 2010-11-20
with sudo dhclient eth0

 Internet Systems Consortium DHCP Client V3.1.2
  Copyright 2004-2008 Internet Systems Consortium.
  All rights reserved.
  For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
   
  Listening on LPF/eth0/c8:0a:a9:6f:a8:34
  Sending on   LPF/eth0/c8:0a:a9:6f:a8:34
  Sending on   Socket/fallback
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
  No DHCPOFFERS received.
  No working leases in persistent database - sleeping.

---

### Post by alex18min on 2010-11-20
Internet Systems Consortium DHCP Client V3.1.2
  Copyright 2004-2008 Internet Systems Consortium.
  All rights reserved.
  For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
   
  Listening on LPF/eth0/c8:0a:a9:6f:a8:34
  Sending on   LPF/eth0/c8:0a:a9:6f:a8:34
  Sending on   Socket/fallback
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
  No DHCPOFFERS received.
  No working leases in persistent database - sleeping.

---

### Post by uncaspi on 2010-11-20
Did you plug in the wire in eth0 ?

---

### Post by alex18min on 2010-11-20
no... what i've to do?

---

### Post by uncaspi on 2010-11-20
You just should get connected with wire first before we try to connect wireless.

---

### Post by alex18min on 2010-11-20
but i cannot, the icon is grey and i can't do anything; it tells me: Wired network disconnected.

---

### Post by uncaspi on 2010-11-20
Can you right click the icon and select edit connections?
Do you see eth0 or auto eth0  ?
If not will you please post the content of /etc/network/interfaces
file?

---

### Post by alex18min on 2010-11-21
ok i can see eth0.
now?
excuse my ignorance, but i'm new in ubuntu.

---

### Post by alex18min on 2010-11-22
problem still not solved! Please help me
thx in advance

---

### Post by uncaspi on 2010-11-22
Choose edit connections eth0 and first try to check Automatic DHCP.
IF it not works tab to ip4-settings and give the info as asked. As DNS you can use 8.8.8.8
The gateway is your router ip-address.

---

