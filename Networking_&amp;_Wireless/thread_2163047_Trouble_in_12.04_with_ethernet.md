---
title: "Trouble in 12.04 with ethernet"
date: 2013-07-16
forum: Networking &amp; Wireless
---

### Post by armstri on 2013-07-16
All,

I am having trouble with ethernet in 12.04.  It worked when I initially ran the livecd. I then installed, and had the install perform updates.  Once it booted into the newly installed OS I had no connectivity. And now I have no connectivity in the livecd.  Any thoughts?  Let me know what would be useful to see


This is from the syslog
```
an@MEDIA-CENTER:~$ tail -f /var/log/syslog
Jul 16 19:34:18 MEDIA-CENTER dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jul 16 19:34:24 MEDIA-CENTER dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jul 16 19:34:30 MEDIA-CENTER dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Jul 16 19:34:31 MEDIA-CENTER NetworkManager[853]: <info> (eth0): IP6 addrconf timed out or failed.
Jul 16 19:34:31 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul 16 19:34:31 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul 16 19:34:31 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jul 16 19:34:32 MEDIA-CENTER dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Jul 16 19:34:41 MEDIA-CENTER dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Jul 16 19:34:44 MEDIA-CENTER dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Jul 16 19:34:53 MEDIA-CENTER dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Jul 16 19:34:54 MEDIA-CENTER dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jul 16 19:34:56 MEDIA-CENTER NetworkManager[853]: <warn> (eth0): DHCPv4 request timed out.
Jul 16 19:34:56 MEDIA-CENTER NetworkManager[853]: <info> (eth0): canceled DHCP transaction, DHCP client pid 3636
Jul 16 19:34:56 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Jul 16 19:34:56 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Jul 16 19:34:56 MEDIA-CENTER NetworkManager[853]: <info> (eth0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Jul 16 19:34:56 MEDIA-CENTER NetworkManager[853]: <warn> Activation (eth0) failed.
Jul 16 19:34:56 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Jul 16 19:34:56 MEDIA-CENTER NetworkManager[853]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jul 16 19:34:56 MEDIA-CENTER NetworkManager[853]: <info> (eth0): deactivating device (reason 'none') [0]
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> Auto-activating connection 'Wired connection 1'.
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) starting connection 'Wired connection 1'
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> dhclient started with pid 3729
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Beginning IP6 addrconf.
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jul 16 19:34:59 MEDIA-CENTER dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jul 16 19:34:59 MEDIA-CENTER dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jul 16 19:34:59 MEDIA-CENTER dhclient: All rights reserved.
Jul 16 19:34:59 MEDIA-CENTER dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul 16 19:34:59 MEDIA-CENTER dhclient: 
Jul 16 19:34:59 MEDIA-CENTER NetworkManager[853]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jul 16 19:34:59 MEDIA-CENTER dhclient: Listening on LPF/eth0/00:1e:8c:9e:7e:16
Jul 16 19:34:59 MEDIA-CENTER dhclient: Sending on   LPF/eth0/00:1e:8c:9e:7e:16
Jul 16 19:34:59 MEDIA-CENTER dhclient: Sending on   Socket/fallback
Jul 16 19:34:59 MEDIA-CENTER dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 16 19:35:01 MEDIA-CENTER dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jul 16 19:35:02 MEDIA-CENTER dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jul 16 19:35:09 MEDIA-CENTER dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Jul 16 19:35:15 MEDIA-CENTER dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Jul 16 19:35:19 MEDIA-CENTER NetworkManager[853]: <info> (eth0): IP6 addrconf timed out or failed.
Jul 16 19:35:19 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul 16 19:35:19 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul 16 19:35:19 MEDIA-CENTER NetworkManager[853]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jul 16 19:35:24 MEDIA-CENTER dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Jul 16 19:35:31 MEDIA-CENTER dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11





```

Thanks
Ian

---

### Post by TheFu on 2013-07-16
It looks to me like a bad cable or dead switch port.   I'd try  reseating the cable first, then replacing it.

---

### Post by armstri on 2013-07-16
I tried reseating the cable, with no luck.  And then replaced it.  Still no luck.  Do you mean a potentially bad ethernet port on the motherboard?  Prior to installing ubuntu I had ethernet working in Windows XP

---

