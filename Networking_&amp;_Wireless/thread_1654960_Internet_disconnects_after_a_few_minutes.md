---
title: "Internet disconnects after a few minutes"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by HMD69 on 2010-12-29
Hi all,
After a few minutes(randomly) of login into my account I cannot connect to internet anymore.I use Ethernet and modem is configured properly.I tried restarting modem but doesn't solve the problem.also restarted network-manager but after restarting, It doesn't connect to Ethernet anymore.logging out also doesnt't solve it.

This is the log of "daemon.log" when I try to restart network-manager(or reconnect):

```

NetworkManager[1060]: <info> (eth0): DHCPv4 state changed nbi -> preinit
dhclient: Listening on LPF/eth0/f0:4d:a2:a5:b4:2a
Ddhclient: Sending on   LPF/eth0/f0:4d:a2:a5:b4:2a
dhclient: Sending on   Socket/fallback
dhclient: DHCPREQUEST of 192.168.125.2 on eth0 to 255.255.255.255 port 67
dhclient: DHCPREQUEST of 192.168.125.2 on eth0 to 255.255.255.255 port 67
dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
NetworkManager[1060]: <warn> (eth0): DHCPv4 request timed out.
NetworkManager[1060]: <info> (eth0): canceled DHCP transaction, DHCP client pid 4059
NetworkManager[1060]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
NetworkManager[1060]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
NetworkManager[1060]: <info> (eth0): device state change: 7 -> 9 (reason 5)
NetworkManager[1060]: <info> Marking connection 'Auto eth0' invalid.
NetworkManager[1060]: <warn> Activation (eth0) failed.
NetworkManager[1060]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
NetworkManager[1060]: <info> (eth0): device state change: 9 -> 3 (reason 0)
NetworkManager[1060]: <info> (eth0): deactivating device (reason: 0).

```

Does it contain any helpful info?
Thanks in advance

---

