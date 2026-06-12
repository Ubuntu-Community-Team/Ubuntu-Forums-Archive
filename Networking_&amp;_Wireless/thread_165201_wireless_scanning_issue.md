---
title: "wireless scanning issue"
date: 2006-04-24
forum: Networking &amp; Wireless
---

### Post by quintok on 2006-04-24
I seem to be having trouble scanning for my router from my wireless NIC.
I've followed the ndiswrapper wiki document up until 'Loading new driver module'
here's the output from the section of 'loading new driver module' within the wiki.
> quintok@Quintok:~$ sudo depmod -a
quintok@Quintok:~$ sudo modprobe ndiswrapper
quintok@Quintok:~$ tail /var/log/messages
Apr 24 18:49:26 localhost kernel: [4294715.108000] lo: Disabled Privacy Extensions
Apr 24 18:49:26 localhost kernel: [4294715.109000] IPv6 over IPv4 tunneling driver
Apr 24 18:49:29 localhost gconfd (quintok-4981): Resolved address "xml:readwrite:/home/quintok/.gconf" to a writable configuration source at position 0
Apr 24 18:54:49 localhost kernel: [4295038.902000] eth2: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 24 19:09:06 localhost -- MARK --
Apr 24 19:29:06 localhost -- MARK --
Apr 24 19:49:06 localhost -- MARK --
Apr 24 20:09:06 localhost -- MARK --
Apr 24 20:29:07 localhost -- MARK --
Apr 24 20:33:32 localhost kernel: [4300962.760000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
quintok@Quintok:~$ sudo ifdown eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:11:50:06:cf:11
Sending on   LPF/eth1/00:11:50:06:cf:11
Sending on   Socket/fallback
quintok@Quintok:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:11:50:06:cf:11
Sending on   LPF/eth1/00:11:50:06:cf:11
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
quintok@Quintok:~$

just so you see my setup is fine here is ndiswrapper, iwlist and iwconfig's output.
> quintok@Quintok:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
quintok@Quintok:~$ iwlist scan
lo        Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.

quintok@Quintok:~$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"belkin54g"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off

sit0      no wireless extensions.

quintok@Quintok:~$
Thanks for your help
-Q

*edit* I'm running Dapper Beta.

---

