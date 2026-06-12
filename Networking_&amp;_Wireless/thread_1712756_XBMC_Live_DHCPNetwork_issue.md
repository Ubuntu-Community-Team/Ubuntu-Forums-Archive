---
title: "XBMC Live DHCP/Network issue"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by Flerpje on 2011-03-23
First off, since i'm new here, hi everybody! Twenty-something old male here, currently studying Computer Science and took the plunge into Linux recently ;)

I'm a user of XBMC Live and i've been trying to get my network to work! Recently i had XBMCLive working completely, but that was before i chmod'ed my entire disk to someone other than root....commence re-install!

During the install i was prompted for network configuration. I'm 100% sure my network is functioning like it should but yet DHCP configuration failed. No sweat, i'll just it manually later, or so i thought.

Some searching on this forum led me to a solution: edit the config file /etc/network/interfaces and restart the networking service. And guess what? Enabling DHCP here gave me DHCP acces and everything worked, including SSH. However i did this by hitting alt+f1, and when i het alt+f7 to go back into XBMC, my connection crashed again :S When in 'text mode' everything seems to work fine, but as soon as i switch back to the XBMC gui my netwerk settings seem to disappear, even ssh stops working.

When i restart the service manually, everything works perfectly:
```
Listening on LPF/eth0/bc:ae:c5:8f:6f:0e
Sending on   LPF/eth0/bc:ae:c5:8f:6f:0e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.111 from 192.168.1.1
DHCPREQUEST of 192.168.1.111 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.111 from 192.168.1.1
bound to 192.168.1.111 -- renewal in 41303 seconds.
ssh stop/waiting
ssh start/running, process 2254
```

But when the service is started after a reboot, the following output is given:
```
ar 21 21:20:50 (none) dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Mar 21 21:20:57 (none) dhclient: No DHCPOFFERS received.
Mar 21 21:20:57 (none) dhclient: No working leases in persistent database - sleeping.
```

-lshw -C Network output:
```
*-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 03
       serial: bc:ae:c5:8f:6f:0e
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom etherne physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversin=2.3LK-NAPI duplex=full ip=192.168.1.111 latency=0 link=yes multicast=yes portMII speed=10MB/s
       resources: irq:26 ioport:e800(size=256) memory:f8fff000-f8ffffff(prefetcable) memory:f8ff8000-f8ffbfff(prefetchable) memory:fbff0000-fbffffff(prefetchale)
```

What could this possibly be? I'm at a loss here..

---

