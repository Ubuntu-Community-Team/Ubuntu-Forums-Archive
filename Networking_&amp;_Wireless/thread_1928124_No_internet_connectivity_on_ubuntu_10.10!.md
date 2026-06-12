---
title: "No internet connectivity on ubuntu 10.10!"
date: 2012-02-19
forum: Networking &amp; Wireless
---

### Post by southsid3 on 2012-02-19
Hi guys, I have installed Ubuntu 10.10 inside my windows 7 x64
and everything works fine, except Internet.
So the problem is that i cannot connect to internet. 
I have created a DSL connection with my username and password but it says that cable is not plugged in and it is not connecting.

Help please!
Thanks (:

---

### Post by winh8r on 2012-02-19
I have assumed that by "inside" you mean in a virtual box environment?

If so then this might help you:

[https://forums.virtualbox.org/viewtopic.php?t=21907]("https://forums.virtualbox.org/viewtopic.php?t=21907")

---

### Post by southsid3 on 2012-02-19
> **winh8r said:**
> I have assumed that by "inside" you mean in a virtual box environment?

If so then this might help you:

[https://forums.virtualbox.org/viewtopic.php?t=21907]("https://forums.virtualbox.org/viewtopic.php?t=21907")
No, I installed it along my Windows, it is Dual Booting, but when i try to connect to internet, it looks like cable is unplugged :S

---

### Post by Iowan on 2012-02-19
My DSL modem acted like a router, so all I needed to do was let my machine get a DHCP connection. Does **ifconfig -a** show an IP address for the interface? If not, what does **sudo lshw -C networking** show?

---

### Post by southsid3 on 2012-02-19
> **Iowan said:**
> My DSL modem acted like a router, so all I needed to do was let my machine get a DHCP connection. Does **ifconfig -a** show an IP address for the interface? If not, what does **sudo lshw -C networking** show?

Sorry but i'm new in ubuntu and i can't speak english very good, but
when i type in terminal ifconfig -a it shows:

lo Link encap:Local Loopback
                       inet6 addr:  :: 127.0.0.1 Mask:255.0.0.0
                       inet6 addr: ::1/128 Scope:Host
                       UP LOOPBACK RUNNING   MTU:16436  Metric:1
                       RX packets:76 errors:0 dropped:0 overruns:0 frame:0
                       TX packets: 76 errors:0 dropped:0 ovverruns:0 carrier:0
                       collisions:0 txqueuelen:0
                       RX bytes:5840 (5.8 KB) TX bytes:584 (5.8 KB)

wlan0              Link encap:Ethernet HWaddr ********************
                       UP BROADCAST MULTICAST MTU:1500 Metric:1
                       RX packets:76 errors:0 dropped:0 overruns:0 frame:0
                       TX packets: 76 errors:0 dropped:0 ovverruns:0 carrier:0
                       collisions:0 txqueuelen:1000
                       RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

And sudo lshw -C networking shows:
PCI (sysfs)

---

### Post by roelforg on 2012-02-20
First of all, you're not letting lshw finish, the PCI (sysfs) message is because it's still scanning your hw (can take some time). EDIT: The command is: lshw -C network
Also, try: sudo dhclient wlan0
Good luck, i'm better in probs with wired nets, as that's all i have and my setup is rather weired so i've had my cup of net probs.Currently, everything in my room humms along just fine with 30-70 mb local transfers (those limits are because my hd's are slow, the net supports up to 90mb).

---

### Post by Iowan on 2012-02-20
> **roelforg said:**
>  EDIT: The command is: lshw -C network

:oops: OOPS!!!  Seemed wrong when I was typing it...

---

### Post by southsid3 on 2012-02-21
> **roelforg said:**
> First of all, you're not letting lshw finish, the PCI (sysfs) message is because it's still scanning your hw (can take some time). EDIT: The command is: lshw -C network
Also, try: sudo dhclient wlan0
Good luck, i'm better in probs with wired nets, as that's all i have and my setup is rather weired so i've had my cup of net probs.Currently, everything in my room humms along just fine with 30-70 mb local transfers (those limits are because my hd's are slow, the net supports up to 90mb).

ok guys, here is what i see now..
when i type in terminal ifconfig -a it shows:

lo                Link encap:Local Loopback
                   inet6 addr: :: 127.0.0.1 Mask:255.0.0.0
                   inet6 addr: ::1/128 Scope:Host
                   UP LOOPBACK RUNNING MTU:16436 Metric:1
                   RX packets:76 errors:0 dropped:0 overruns:0 frame:0
                   TX packets: 76 errors:0 dropped:0 ovverruns:0 carrier:0
                   collisions:0 txqueuelen:0
                   RX bytes:5840 (5.8 KB) TX bytes:584 (5.8 KB)

wlan0          Link encap:Ethernet HWaddr ************(mac add)
                   UP BROADCAST MULTICAST MTU:1500 Metric:1
                   RX packets:76 errors:0 dropped:0 overruns:0 frame:0
                   TX packets: 76 errors:0 dropped:0 ovverruns:0 carrier:0
                   collisions:0 txqueuelen:1000
                   RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet    HWaddr  ************(mac add)
                    inet  add:169.254.8.248     Bcast:169.254.255.255    Mask:255.255.0.0
                    UP BROADCAST MULTICAST   MTU:1500   Metric:1


The command: lshw -C network  shows:

WARNING: you should run this program as super-user.
 *-network
          descrption:Wireless interface
          product:   AR9285 Wireless Network Adapter (PCI-Express)
          vendor: Atheros Communication Inc.
          physical id: 0
          bus info: pci@0000:02:00.0
          logical name: wlan0
          version: 01
          serial: ************(mac add)
          width: 64 bits
          clock: 33MHz
         capabilities: bus_master cap_list ethernet physical wireless
         configuration: broadcast=yes  driver=ath9k  drivervesion=2.6.35-22-genetic
firmware=N/A  latency=0  multicast=yes  wireless=IEEE 802.11bgn
         resources: irq:17 memory:de800000-de80ffff
 *-network UNCLAIMED
         description: Ethernet controller
         product: Atheros Communication
         vendor: Atheros Communication
         physical id: 0
         bus info: pci@0000:04:00.0
         version: c0
         width:  64 bits
         clock:  33MHz
         capabilities: bus_master  cap_list
         configuration:  latency=0
         resources: memory"dd400000-dd43dddd ioport:a000(size=128)


The command:  sudo dhclient wlan0   shows:

There is already a pid file /var/run/dhcpclient.pid witg pid 2012
killed old client process, removed PID file
Internet System Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet System Consortium.
All rights reserved.
For info, please visit [www.isc.org/software/dhcp/](www.isc.org/software/dhcp/)

Listening on LPF/wlan0/***********(mac add)
Sending on  LPF/wlan0/***********(mac add)
Sending on  Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval  3
No DHCPOFFERS received.
No networking leases in persistent database - sleeping.

---

### Post by roelforg on 2012-02-22
> **southsid3 said:**
> ok guys, here is what i see now..
when i type in terminal ifconfig -a it shows:

lo                Link encap:Local Loopback
                   inet6 addr: :: 127.0.0.1 Mask:255.0.0.0
                   inet6 addr: ::1/128 Scope:Host
                   UP LOOPBACK RUNNING MTU:16436 Metric:1
                   RX packets:76 errors:0 dropped:0 overruns:0 frame:0
                   TX packets: 76 errors:0 dropped:0 ovverruns:0 carrier:0
                   collisions:0 txqueuelen:0
                   RX bytes:5840 (5.8 KB) TX bytes:584 (5.8 KB)

wlan0          Link encap:Ethernet HWaddr ************(mac add)
                   UP BROADCAST MULTICAST MTU:1500 Metric:1
                   RX packets:76 errors:0 dropped:0 overruns:0 frame:0
                   TX packets: 76 errors:0 dropped:0 ovverruns:0 carrier:0
                   collisions:0 txqueuelen:1000
                   RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet    HWaddr  ************(mac add)
                    inet  add:169.254.8.248     Bcast:169.254.255.255    Mask:255.255.0.0
                    UP BROADCAST MULTICAST   MTU:1500   Metric:1


The command: lshw -C network  shows:

WARNING: you should run this program as super-user.
 *-network
          descrption:Wireless interface
          product:   AR9285 Wireless Network Adapter (PCI-Express)
          vendor: Atheros Communication Inc.
          physical id: 0
          bus info: pci@0000:02:00.0
          logical name: wlan0
          version: 01
          serial: ************(mac add)
          width: 64 bits
          clock: 33MHz
         capabilities: bus_master cap_list ethernet physical wireless
         configuration: broadcast=yes  driver=ath9k  drivervesion=2.6.35-22-genetic
firmware=N/A  latency=0  multicast=yes  wireless=IEEE 802.11bgn
         resources: irq:17 memory:de800000-de80ffff
 *-network UNCLAIMED
         description: Ethernet controller
         product: Atheros Communication
         vendor: Atheros Communication
         physical id: 0
         bus info: pci@0000:04:00.0
         version: c0
         width:  64 bits
         clock:  33MHz
         capabilities: bus_master  cap_list
         configuration:  latency=0
         resources: memory"dd400000-dd43dddd ioport:a000(size=128)


The command:  sudo dhclient wlan0   shows:

There is already a pid file /var/run/dhcpclient.pid witg pid 2012
killed old client process, removed PID file
Internet System Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet System Consortium.
All rights reserved.
For info, please visit [www.isc.org/software/dhcp/]("http://www.isc.org/software/dhcp/")

Listening on LPF/wlan0/***********(mac add)
Sending on  LPF/wlan0/***********(mac add)
Sending on  Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval  3
No DHCPOFFERS received.
No networking leases in persistent database - sleeping.
You forgot to use sudo for lshw.

It's rather weired, i don't really excell in WiFi so i'm at a loss here...

---

