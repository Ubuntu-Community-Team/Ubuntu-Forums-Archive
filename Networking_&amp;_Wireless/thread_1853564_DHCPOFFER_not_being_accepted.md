---
title: "DHCPOFFER not being accepted"
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by swook on 2011-10-02
I have searched high and low online and have not been able to find a solution to my problem.
Simply put, my problem is that I cannot make use of DHCP servers for some strange reason.
I can connect to networks fine when I setup manual dhcp, but whatever the interface is, I cannot seem to be able to accept DHCPOFFERs.

Below is an example output:
[INDENT][SIZE="2"]Oct  3 01:56:53 MyHostname NetworkManager[1460]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  3 01:56:53 MyHostname dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  3 01:56:53 MyHostname dhclient: Copyright 2004-2010 Internet Systems Consortium.
Oct  3 01:56:53 MyHostname dhclient: All rights reserved.
Oct  3 01:56:53 MyHostname dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Oct  3 01:56:53 MyHostname dhclient: 
Oct  3 01:56:53 MyHostname NetworkManager[1460]: <info> dhclient started with pid 1027
Oct  3 01:56:53 MyHostname NetworkManager[1460]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Oct  3 01:56:53 MyHostname NetworkManager[1460]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Oct  3 01:56:53 MyHostname dhclient: Listening on LPF/wlan0/MA:CA:DD:RE:SS:OB
Oct  3 01:56:53 MyHostname dhclient: Sending on   LPF/wlan0/MA:CA:DD:RE:SS:OB
Oct  3 01:56:53 MyHostname dhclient: Sending on   Socket/fallback
Oct  3 01:56:53 MyHostname dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct  3 01:56:54 MyHostname dhclient: DHCPOFFER from 192.168.1.1: no broadcast-address option.
Oct  3 01:56:55 MyHostname dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct  3 01:56:55 MyHostname dhclient: DHCPOFFER from 192.168.1.1: no broadcast-address option.
Oct  3 01:56:56 MyHostname dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct  3 01:56:56 MyHostname dhclient: DHCPOFFER from 192.168.1.1: no broadcast-address option.
Oct  3 01:57:00 MyHostname dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct  3 01:57:00 MyHostname dhclient: DHCPOFFER from 192.168.1.1: no broadcast-address option.
Oct  3 01:57:08 MyHostname dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct  3 01:57:08 MyHostname dhclient: DHCPOFFER from 192.168.1.1: no broadcast-address option.
Oct  3 01:57:16 MyHostname dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct  3 01:57:17 MyHostname dhclient: DHCPOFFER from 192.168.1.1: no broadcast-address option.
Oct  3 01:57:27 MyHostname dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Oct  3 01:57:27 MyHostname dhclient: DHCPOFFER from 192.168.1.1: no broadcast-address option.
Oct  3 01:57:39 MyHostname NetworkManager[1460]: <warn> (wlan0): DHCPv4 request timed out.
Oct  3 01:57:39 MyHostname NetworkManager[1460]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1027[/SIZE][/INDENT]

NetworkManager seems to be using `dhclient` from the package `isc-dhcp-client`.
I am running Kubuntu 11.04, NetworkManager 0.8.4, interfacing with KDE's plasma-widget-networkmanagement.


**_Edit: Found fix_**
DHCPOFFER was not being accepted because a few lines had somehow made it into my `/etc/dhcp/dhclient.conf`.
I probably accidentally copy&pasted an incorrect example in a long time ago.

The problematic config:
[indent]#require subnet-mask, broadcast-address, time-offset, routers,
#       domain-name, domain-search, host-name,
#       netbios-name-servers, netbios-scope, interface-mtu,
#       rfc3442-classless-static-routes, ntp-servers;[/indent]

---

