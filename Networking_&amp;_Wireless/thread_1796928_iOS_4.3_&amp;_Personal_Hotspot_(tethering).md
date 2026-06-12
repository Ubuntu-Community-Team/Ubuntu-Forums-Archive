---
title: "iOS 4.3 &amp; Personal Hotspot (tethering)"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by willskills on 2011-07-04
Hi folks,

So I upgraded my iOS on my iPhone 3GS to 4.3, which allows for "personal hotspot tethering".

The version before this simply allowed for tethering, and it worked really well, just plug my phone in via usb and I'd be able to connect to the internet no problem.

Since the iOS upgrade, this seems to fail, here's a quick pertinent snippet:

tail -f /var/log/syslog

Jul  4 10:10:38 alba kernel: [  209.560127] usb 1-3: new high speed USB device using ehci_hcd and address 4
Jul  4 10:10:39 alba kernel: [  209.934884] ipheth 1-3:4.2: Apple iPhone USB Ethernet device attached
Jul  4 10:10:39 alba NetworkManager[552]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:4.2/net/eth1, iface: eth1)
Jul  4 10:10:39 alba NetworkManager[552]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:4.2/net/eth1, iface: eth1): no ifupdown configuration found.
Jul  4 10:10:39 alba NetworkManager[552]: <error> [1309799439.310944] [nm-device-ethernet.c:763] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Jul  4 10:10:39 alba NetworkManager[552]: <info> (eth1): carrier is OFF
Jul  4 10:10:39 alba NetworkManager[552]: <info> (eth1): new Ethernet device (driver: 'ipheth' ifindex: 6)
Jul  4 10:10:39 alba NetworkManager[552]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/3
Jul  4 10:10:39 alba NetworkManager[552]: <info> (eth1): now managed
Jul  4 10:10:39 alba NetworkManager[552]: <info> (eth1): device state change: 1 -> 2 (reason 2)
Jul  4 10:10:39 alba NetworkManager[552]: <info> (eth1): bringing up device.
Jul  4 10:10:39 alba NetworkManager[552]: <info> (eth1): preparing device.
Jul  4 10:10:39 alba NetworkManager[552]: <info> (eth1): deactivating device (reason: 2).
Jul  4 10:10:39 alba NetworkManager[552]: <info> Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:4.2/net/eth1
Jul  4 10:10:39 alba NetworkManager[552]: <info> (eth1): carrier now ON (device state 2)
Jul  4 10:10:39 alba NetworkManager[552]: <info> (eth1): device state change: 2 -> 3 (reason 40)
Jul  4 10:10:39 alba NetworkManager[552]: <info> Activation (eth1) starting connection 'Auto eth1'
Jul  4 10:10:39 alba NetworkManager[552]: <info> (eth1): device state change: 3 -> 4 (reason 0)
Jul  4 10:10:39 alba NetworkManager[552]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jul  4 10:10:39 alba NetworkManager[552]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jul  4 10:10:39 alba NetworkManager[552]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jul  4 10:10:39 alba NetworkManager[552]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jul  4 10:10:39 alba NetworkManager[552]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jul  4 10:10:39 alba NetworkManager[552]: <info> (eth1): device state change: 4 -> 5 (reason 0)
Jul  4 10:10:39 alba NetworkManager[552]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Jul  4 10:10:39 alba NetworkManager[552]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Jul  4 10:10:39 alba NetworkManager[552]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jul  4 10:10:39 alba NetworkManager[552]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Jul  4 10:10:39 alba NetworkManager[552]: <info> (eth1): device state change: 5 -> 7 (reason 0)
Jul  4 10:10:39 alba NetworkManager[552]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul  4 10:10:39 alba NetworkManager[552]: <info> dhclient started with pid 2102
Jul  4 10:10:39 alba NetworkManager[552]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Jul  4 10:10:39 alba dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Jul  4 10:10:39 alba dhclient: Copyright 2004-2010 Internet Systems Consortium.
Jul  4 10:10:39 alba dhclient: All rights reserved.
Jul  4 10:10:39 alba dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jul  4 10:10:39 alba dhclient: 
Jul  4 10:10:39 alba NetworkManager[552]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Jul  4 10:10:39 alba dhclient: Listening on LPF/eth1/02:26:08:a9:cb:34
Jul  4 10:10:39 alba dhclient: Sending on   LPF/eth1/02:26:08:a9:cb:34
Jul  4 10:10:39 alba dhclient: Sending on   Socket/fallback
Jul  4 10:10:39 alba dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Jul  4 10:10:40 alba avahi-daemon[541]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::26:8ff:fea9:cb34.
Jul  4 10:10:40 alba avahi-daemon[541]: New relevant interface eth1.IPv6 for mDNS.
Jul  4 10:10:40 alba avahi-daemon[541]: Registering new address record for fe80::26:8ff:fea9:cb34 on eth1.*.
Jul  4 10:10:42 alba dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Jul  4 10:10:49 alba kernel: [  220.096027] eth1: no IPv6 routers present
Jul  4 10:10:50 alba dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Jul  4 10:11:01 alba dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
Jul  4 10:11:22 alba dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Jul  4 10:11:24 alba NetworkManager[552]: <warn> (eth1): DHCPv4 request timed out.
Jul  4 10:11:24 alba NetworkManager[552]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2102
Jul  4 10:11:24 alba NetworkManager[552]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jul  4 10:11:24 alba NetworkManager[552]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) started...
Jul  4 10:11:24 alba NetworkManager[552]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul  4 10:11:24 alba NetworkManager[552]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jul  4 10:11:24 alba NetworkManager[552]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Jul  4 10:11:24 alba NetworkManager[552]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Jul  4 10:11:24 alba NetworkManager[552]: <info> (eth1): device state change: 7 -> 9 (reason 5)
Jul  4 10:11:24 alba NetworkManager[552]: <info> Marking connection 'Auto eth1' invalid.
Jul  4 10:11:24 alba NetworkManager[552]: <warn> Activation (eth1) failed.
Jul  4 10:11:24 alba NetworkManager[552]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Jul  4 10:11:24 alba NetworkManager[552]: <info> (eth1): device state change: 9 -> 3 (reason 0)
Jul  4 10:11:24 alba NetworkManager[552]: <info> (eth1): deactivating device (reason: 0).

After attempting to connect for a while, it drops out and says "wired network disconnected".

Can anyone provide any assistance based on the info above? If not, what more would you need to see?

Thanks kindly for any ideas!

---

### Post by willskills on 2011-08-04
No updates to any packages, but latest kernel seemed to fix this. I can't say that's the definitive fix - so I am not marking as solved - but in case anyone else comes across this issue!

---

