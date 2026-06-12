---
title: "Wired connection slow to connect"
date: 2013-04-16
forum: Networking &amp; Wireless
---

### Post by NautiusMaximus on 2013-04-16
I have recently had long waits (several minutes) for my computer to connect to the network via a wired connection when I switch it on in the morning. Once it's connected, the connection works just fine, but it takes a long time to make the connection.

Here's an extract from the syslog at the time when it's trying:

```
Apr 16 09:08:16 DMUD01 kernel: [  224.399943] r8169 0000:03:00.0: eth0: link up
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> (eth0): carrier now ON (device state 20)
Apr 16 09:08:16 DMUD01 kernel: [  224.404933] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> Auto-activating connection 'Wired connection 1'.
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> Activation (eth0) starting connection 'Wired connection 1'
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> dhclient started with pid 2374
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> Activation (eth0) Beginning IP6 addrconf.
Apr 16 09:08:16 DMUD01 dhclient: Internet Systems Consortium DHCP Client 4.2.4
Apr 16 09:08:16 DMUD01 dhclient: Copyright 2004-2012 Internet Systems Consortium.
Apr 16 09:08:16 DMUD01 dhclient: All rights reserved.
Apr 16 09:08:16 DMUD01 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr 16 09:08:16 DMUD01 dhclient: 
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 16 09:08:16 DMUD01 NetworkManager[853]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Apr 16 09:08:16 DMUD01 dhclient: Listening on LPF/eth0/90:2b:34:96:31:93
Apr 16 09:08:16 DMUD01 dhclient: Sending on   LPF/eth0/90:2b:34:96:31:93
Apr 16 09:08:16 DMUD01 dhclient: Sending on   Socket/fallback
Apr 16 09:08:16 DMUD01 dhclient: DHCPREQUEST of 192.168.98.66 on eth0 to 255.255.255.255 port 67
Apr 16 09:08:17 DMUD01 kernel: [  225.517351] r8169 0000:03:00.0: eth0: link down
Apr 16 09:08:17 DMUD01 NetworkManager[853]: <info> (eth0): carrier now OFF (device state 70, deferring action for 4 seconds)
Apr 16 09:08:17 DMUD01 avahi-daemon[881]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::922b:34ff:fe96:3193.
Apr 16 09:08:17 DMUD01 avahi-daemon[881]: New relevant interface eth0.IPv6 for mDNS.
Apr 16 09:08:17 DMUD01 avahi-daemon[881]: Registering new address record for fe80::922b:34ff:fe96:3193 on eth0.*.
Apr 16 09:08:19 DMUD01 dhclient: DHCPREQUEST of 192.168.98.66 on eth0 to 255.255.255.255 port 67
Apr 16 09:08:19 DMUD01 kernel: [  227.594387] r8169 0000:03:00.0: eth0: link up
Apr 16 09:08:19 DMUD01 NetworkManager[853]: <info> (eth0): carrier now ON (device state 70)
Apr 16 09:08:21 DMUD01 kernel: [  228.766317] r8169 0000:03:00.0: eth0: link down
Apr 16 09:08:21 DMUD01 NetworkManager[853]: <info> (eth0): carrier now OFF (device state 70, deferring action for 4 seconds)
Apr 16 09:08:23 DMUD01 kernel: [  230.918790] r8169 0000:03:00.0: eth0: link up
Apr 16 09:08:23 DMUD01 NetworkManager[853]: <info> (eth0): carrier now ON (device state 70)
Apr 16 09:08:24 DMUD01 kernel: [  232.015262] r8169 0000:03:00.0: eth0: link down
Apr 16 09:08:24 DMUD01 NetworkManager[853]: <info> (eth0): carrier now OFF (device state 70, deferring action for 4 seconds)
Apr 16 09:08:24 DMUD01 dhclient: DHCPREQUEST of 192.168.98.66 on eth0 to 255.255.255.255 port 67
Apr 16 09:08:26 DMUD01 kernel: [  234.167731] r8169 0000:03:00.0: eth0: link up
Apr 16 09:08:26 DMUD01 NetworkManager[853]: <info> (eth0): carrier now ON (device state 70)
Apr 16 09:08:27 DMUD01 kernel: [  235.264206] r8169 0000:03:00.0: eth0: link down
Apr 16 09:08:27 DMUD01 NetworkManager[853]: <info> (eth0): carrier now OFF (device state 70, deferring action for 4 seconds)
Apr 16 09:08:29 DMUD01 kernel: [  237.418669] r8169 0000:03:00.0: eth0: link up
Apr 16 09:08:29 DMUD01 NetworkManager[853]: <info> (eth0): carrier now ON (device state 70)
Apr 16 09:08:30 DMUD01 kernel: [  238.510506] r8169 0000:03:00.0: eth0: link down
Apr 16 09:08:30 DMUD01 NetworkManager[853]: <info> (eth0): carrier now OFF (device state 70, deferring action for 4 seconds)
Apr 16 09:08:32 DMUD01 kernel: [  240.694963] r8169 0000:03:00.0: eth0: link up
Apr 16 09:08:32 DMUD01 NetworkManager[853]: <info> (eth0): carrier now ON (device state 70)
Apr 16 09:08:34 DMUD01 kernel: [  241.885238] r8169 0000:03:00.0: eth0: link down
Apr 16 09:08:34 DMUD01 NetworkManager[853]: <info> (eth0): carrier now OFF (device state 70, deferring action for 4 seconds)
Apr 16 09:08:36 DMUD01 kernel: [  244.007836] r8169 0000:03:00.0: eth0: link up
Apr 16 09:08:36 DMUD01 NetworkManager[853]: <info> (eth0): carrier now ON (device state 70)
Apr 16 09:08:36 DMUD01 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 16 09:08:37 DMUD01 NetworkManager[853]: <info> (eth0): IP6 addrconf timed out or failed.
Apr 16 09:08:37 DMUD01 NetworkManager[853]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 16 09:08:37 DMUD01 NetworkManager[853]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 16 09:08:37 DMUD01 NetworkManager[853]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Apr 16 09:08:37 DMUD01 kernel: [  245.134150] r8169 0000:03:00.0: eth0: link down
Apr 16 09:08:37 DMUD01 NetworkManager[853]: <info> (eth0): carrier now OFF (device state 70, deferring action for 4 seconds)
Apr 16 09:08:39 DMUD01 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr 16 09:08:39 DMUD01 kernel: [  247.268282] r8169 0000:03:00.0: eth0: link up
Apr 16 09:08:39 DMUD01 NetworkManager[853]: <info> (eth0): carrier now ON (device state 70)
Apr 16 09:08:40 DMUD01 kernel: [  248.383176] r8169 0000:03:00.0: eth0: link down
Apr 16 09:08:40 DMUD01 NetworkManager[853]: <info> (eth0): carrier now OFF (device state 70, deferring action for 4 seconds)
Apr 16 09:08:42 DMUD01 kernel: [  250.472184] r8169 0000:03:00.0: eth0: link up
Apr 16 09:08:42 DMUD01 NetworkManager[853]: <info> (eth0): carrier now ON (device state 70)
Apr 16 09:08:43 DMUD01 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 16 09:08:43 DMUD01 kernel: [  251.629408] r8169 0000:03:00.0: eth0: link down
Apr 16 09:08:43 DMUD01 NetworkManager[853]: <info> (eth0): carrier now OFF (device state 70, deferring action for 4 seconds)
Apr 16 09:08:45 DMUD01 kernel: [  253.721086] r8169 0000:03:00.0: eth0: link up
Apr 16 09:08:46 DMUD01 NetworkManager[853]: <info> (eth0): carrier now ON (device state 70)
Apr 16 09:08:47 DMUD01 kernel: [  254.878388] r8169 0000:03:00.0: eth0: link down
Apr 16 09:08:47 DMUD01 NetworkManager[853]: <info> (eth0): carrier now OFF (device state 70, deferring action for 4 seconds)
Apr 16 09:08:49 DMUD01 kernel: [  257.170244] r8169 0000:03:00.0: eth0: link up
Apr 16 09:08:49 DMUD01 NetworkManager[853]: <info> (eth0): carrier now ON (device state 70)
Apr 16 09:08:49 DMUD01 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr 16 09:08:50 DMUD01 kernel: [  258.250434] r8169 0000:03:00.0: eth0: link down
Apr 16 09:08:50 DMUD01 NetworkManager[853]: <info> (eth0): carrier now OFF (device state 70, deferring action for 4 seconds)
Apr 16 09:08:52 DMUD01 kernel: [  260.345848] r8169 0000:03:00.0: eth0: link up
Apr 16 09:08:52 DMUD01 NetworkManager[853]: <info> (eth0): carrier now ON (device state 70)
Apr 16 09:08:53 DMUD01 kernel: [  261.499418] r8169 0000:03:00.0: eth0: link down
Apr 16 09:08:53 DMUD01 NetworkManager[853]: <info> (eth0): carrier now OFF (device state 70, deferring action for 4 seconds)
Apr 16 09:08:55 DMUD01 kernel: [  263.605246] r8169 0000:03:00.0: eth0: link up
Apr 16 09:08:55 DMUD01 NetworkManager[853]: <info> (eth0): carrier now ON (device state 70)
Apr 16 09:08:57 DMUD01 kernel: [  264.748365] r8169 0000:03:00.0: eth0: link down
Apr 16 09:08:57 DMUD01 NetworkManager[853]: <info> (eth0): carrier now OFF (device state 70, deferring action for 4 seconds)
Apr 16 09:08:59 DMUD01 kernel: [  266.793410] r8169 0000:03:00.0: eth0: link up
Apr 16 09:08:59 DMUD01 NetworkManager[853]: <info> (eth0): carrier now ON (device state 70)
Apr 16 09:09:00 DMUD01 NetworkManager[853]: <info> (eth0): carrier now OFF (device state 70, deferring action for 4 seconds)
Apr 16 09:09:00 DMUD01 kernel: [  267.871520] r8169 0000:03:00.0: eth0: link down
Apr 16 09:09:02 DMUD01 NetworkManager[853]: <warn> (eth0): DHCPv4 request timed out.
Apr 16 09:09:02 DMUD01 kernel: [  270.025538] r8169 0000:03:00.0: eth0: link up
Apr 16 09:09:02 DMUD01 NetworkManager[853]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2374
Apr 16 09:09:02 DMUD01 NetworkManager[853]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Apr 16 09:09:02 DMUD01 NetworkManager[853]: <info> (eth0): carrier now ON (device state 70)
Apr 16 09:09:02 DMUD01 NetworkManager[853]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Apr 16 09:09:02 DMUD01 NetworkManager[853]: <info> (eth0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Apr 16 09:09:02 DMUD01 NetworkManager[853]: <warn> Activation (eth0) failed for connection 'Wired connection 1'
Apr 16 09:09:02 DMUD01 NetworkManager[853]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Apr 16 09:09:02 DMUD01 NetworkManager[853]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 16 09:09:02 DMUD01 NetworkManager[853]: <info> (eth0): deactivating device (reason 'none') [0]
Apr 16 09:09:02 DMUD01 avahi-daemon[881]: Withdrawing address record for fe80::922b:34ff:fe96:3193 on eth0.
Apr 16 09:09:02 DMUD01 avahi-daemon[881]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::922b:34ff:fe96:3193.
Apr 16 09:09:02 DMUD01 avahi-daemon[881]: Interface eth0.IPv6 no longer relevant for mDNS.
Apr 16 09:09:03 DMUD01 kernel: [  271.120454] r8169 0000:03:00.0: eth0: link down
Apr 16 09:09:03 DMUD01 NetworkManager[853]: <info> (eth0): carrier now OFF (device state 30)
```

I'm hoping there's a clue in there about what might be going wrong for someone who understands more about networking than I do?

I'm using a standard installation of Ubuntu 12.10, 64 bit.

Thanks
NM

---

### Post by NautiusMaximus on 2013-04-30
Bump?

---

### Post by NautiusMaximus on 2013-05-01
A little more information here that might be of help: it seems that when the server from which the PC gets its IP address (a Windows 2003 server) still has a record of the DHCP lease, then my PC can't make a connection at all. If I go onto the server and delete the DHCP lease, then it works, although it's still slow to find the connection.

Any ideas what might be causing the problem?

Thanks
NM

---

### Post by NautiusMaximus on 2013-05-02
Well, I must say it's unusual to get no reply on what is normally such a helpful forum. I'm guessing that it's not because you wonderful folk don't want to help, but I've probably missed out some important information that would allow you to have more of an idea of what's going on.

So what else would you need to know that would help you get to the bottom of my problem? I'd really appreciate some help here: the problem seems to be getting worse, and I'm just not able to get much work done at the start of the day until my PC has found its network connection.

Thanks
NM

---

### Post by sourchier on 2013-05-02
Windows active directory is a very complicated beast. You need to post us some details about the server. Try running dcdiag /test:DNS. Also it is unclear if you have any other issues with the server *. Viruses and fragmentation issues affect many Windows servers. You may need to do some cleaning on your server.
* A dying/misconfigured NIC is also possible.

---

