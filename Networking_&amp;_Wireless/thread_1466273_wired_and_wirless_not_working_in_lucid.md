---
title: "wired and wirless not working in lucid"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by mylo9000 on 2010-04-30
hey all, i'm really frustrated with ubuntu the last little while. i thought things would be better but its hard to stay optimistic when nothing works. 

My wife's laptop an MSI A6000-029US has an nVidia chipset 
[MCP79 (rev b1) according to lspci in lucid].

i expected the RaLink RT3090 not to work out of box.. but the Ethernet controller for the wired connection doesn't work either.
i can't get this thing online to update it.

the syslog says:
```

Apr 30 04:13:39 msilappy NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Apr 30 04:13:39 msilappy NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Apr 30 04:13:39 msilappy kernel: [  402.001626] eth0: link up.
Apr 30 04:13:53 msilappy NetworkManager: <info>  Activation (eth0) starting connection 'Auto Ethernet'
Apr 30 04:13:53 msilappy NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Apr 30 04:13:53 msilappy NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 30 04:13:53 msilappy NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 30 04:13:53 msilappy NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 30 04:13:53 msilappy NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 30 04:13:53 msilappy NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 30 04:13:53 msilappy NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Apr 30 04:13:53 msilappy NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 30 04:13:53 msilappy NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 30 04:13:53 msilappy NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 30 04:13:53 msilappy NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 30 04:13:53 msilappy NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Apr 30 04:13:53 msilappy NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Apr 30 04:13:53 msilappy NetworkManager: <info>  dhclient started with pid 1494
Apr 30 04:13:53 msilappy NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Apr 30 04:13:53 msilappy NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 30 04:13:53 msilappy NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Apr 30 04:13:53 msilappy NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Apr 30 04:13:53 msilappy dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 30 04:13:53 msilappy dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 30 04:13:53 msilappy dhclient: All rights reserved.
Apr 30 04:13:53 msilappy dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr 30 04:13:53 msilappy dhclient: 
Apr 30 04:13:53 msilappy NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Apr 30 04:13:53 msilappy dhclient: Listening on LPF/eth0/40:61:86:1b:1e:8d
Apr 30 04:13:53 msilappy dhclient: Sending on   LPF/eth0/40:61:86:1b:1e:8d
Apr 30 04:13:53 msilappy dhclient: Sending on   Socket/fallback
Apr 30 04:13:57 msilappy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 30 04:14:06 msilappy dhclient: last message repeated 2 times
Apr 30 04:14:06 msilappy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 30 04:14:12 msilappy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 30 04:14:18 msilappy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr 30 04:14:29 msilappy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr 30 04:14:38 msilappy NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
Apr 30 04:14:39 msilappy NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1494
Apr 30 04:14:39 msilappy NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Apr 30 04:14:39 msilappy NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Apr 30 04:14:39 msilappy NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
Apr 30 04:14:39 msilappy NetworkManager: <info>  Marking connection 'Auto Ethernet' invalid.
Apr 30 04:14:39 msilappy NetworkManager: <info>  Activation (eth0) failed.
Apr 30 04:14:39 msilappy NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Apr 30 04:14:39 msilappy NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Apr 30 04:14:39 msilappy NetworkManager: <info>  (eth0): deactivating device (reason: 0).

```

any help would be very much appreciated....



found a solution for the wireless, now i can connect to the net an get updates.
post #21
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)

still would like to know why the Ethernet keeps timing out. would be nice if it worked.

---

### Post by NichoTL on 2010-04-30
Your Ethernet is timing out because you are not getting an answer from the DHCP: is it possible that you have MAC-address filtering enabled on your router?

---

