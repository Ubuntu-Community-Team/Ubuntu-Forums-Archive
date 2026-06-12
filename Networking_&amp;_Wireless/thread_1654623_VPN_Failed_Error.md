---
title: "VPN Failed Error"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by Ckesey on 2010-12-28
I'm trying to get my cisco VPN connection working but have run into issues and looking for some help.

I installed the resolvconf & *network*-*manager*-[I]vpnc which gives the the ability to select Cisco Compatible VPN (vpnc) when created a new VPN. 

After I create it and try to connect I get a generic error "The VPN connection failed"

When I check the /var/log/syslog for message this is the entry with my attempted vpn connection:

Dec 28 15:29:13 ckeseyVGN NetworkManager[982]: <info> Starting VPN service 'org.freedesktop.NetworkManager.vpnc'...
Dec 28 15:29:13 ckeseyVGN NetworkManager[982]: <info> VPN service 'org.freedesktop.NetworkManager.vpnc' started (org.freedesktop.NetworkManager.vpnc), PID 7817
Dec 28 15:29:13 ckeseyVGN NetworkManager[982]: <info> VPN service 'org.freedesktop.NetworkManager.vpnc' appeared, activating connections
Dec 28 15:29:13 ckeseyVGN NetworkManager[982]: <info> VPN plugin state changed: 1
Dec 28 15:29:13 ckeseyVGN NetworkManager[982]: <info> VPN plugin state changed: 3
Dec 28 15:29:13 ckeseyVGN NetworkManager[982]: <info> VPN connection 'VPN connection 1' (Connect) reply received.
Dec 28 15:29:13 ckeseyVGN kernel: [15989.030325] tun0: Disabled Privacy Extensions
Dec 28 15:29:13 ckeseyVGN modem-manager: (net/tun0): could not get port's parent device
Dec 28 15:29:13 ckeseyVGN NetworkManager[982]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Dec 28 15:29:13 ckeseyVGN NetworkManager[982]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Dec 28 15:29:14 ckeseyVGN avahi-daemon[989]: Withdrawing workstation service for tun0.
Dec 28 15:29:14 ckeseyVGN NetworkManager[982]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Dec 28 15:29:14 ckeseyVGN NetworkManager[982]: <warn> VPN plugin failed: 1
Dec 28 15:29:14 ckeseyVGN NetworkManager[982]: <info> VPN plugin state changed: 6
Dec 28 15:29:14 ckeseyVGN NetworkManager[982]: <info> VPN plugin state change reason: 0
Dec 28 15:29:14 ckeseyVGN NetworkManager[982]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Dec 28 15:29:14 ckeseyVGN NetworkManager[982]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Dec 28 15:29:14 ckeseyVGN NetworkManager[982]: <info> Policy set 'Auto Comtrend' (wlan0) as default for IPv4 routing and DNS.
[I]
I have googled a few things above but I haven't been able to correct anything.

Any ideas??[/I]
[/I]

---

### Post by Ckesey on 2010-12-29
Anyone???

I've tried several things found on google searches but same results.......

---

### Post by jamessnell on 2011-02-17
I may be having a related issue.. I'm not totally sure as I've yet to have my VPN connection ever work on Ubuntu (granted, I've spent like an hour total on the problem).

[This bug report]("https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/668874") seems related to me.

---

