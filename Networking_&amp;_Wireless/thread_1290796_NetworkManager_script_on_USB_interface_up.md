---
title: "NetworkManager script on USB interface up"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by jonsmirl on 2009-10-13
I have a USB device that implements ipv6 over 802.15.4. I'm using 9.04. I'd like to get the network to automatically configure when I plug the stick in. I've managed to get radvd work. Now I need to run a command to form the subnet: "ip -6 address add aaaa::1/64 dev usb0"

I placed a small script containing this command in /etc/network/if-up.d. When I plug the card in NetworkManager should see it and run 
/etc/NetworkManager/dispatcher.d/01ifupdown That script in turn calls /etc/network/if-up.d I have manually verified that these scripts properly chain to each other. 

NetworkManager is not calling /etc/NetworkManager/dispatcher.d/01ifupdown when I plug my USB stick in. Any ideas why not?

```
Oct 13 22:22:34 terra NetworkManager: <info>  (usb0): now unmanaged 
Oct 13 22:22:34 terra NetworkManager: <info>  (usb0): device state change: 3 -> 1 
Oct 13 22:22:34 terra NetworkManager: <info>  (usb0): cleaning up... 
Oct 13 22:22:40 terra kernel: usb 3-2: new full speed USB device using uhci_hcd and address 5
Oct 13 22:22:40 terra kernel: usb 3-2: configuration #1 chosen from 1 choice
Oct 13 22:22:40 terra kernel: rndis_host 3-2:1.0: dev can't take 1338 byte packets (max 1338), adjusting MTU to 1280
Oct 13 22:22:40 terra kernel: usb0: register 'rndis_host' at usb-0000:00:1a.1-2, RNDIS device, 02:12:13:14:15:22
Oct 13 22:22:40 terra kernel: cdc_acm 3-2:1.2: ttyACM0: USB ACM device
Oct 13 22:22:40 terra nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_02_12_13_14_15_22, iface: usb0): not well known
Oct 13 22:22:40 terra NetworkManager: <info>  (usb0): new Ethernet device (driver: 'rndis_host') 
Oct 13 22:22:40 terra NetworkManager: <info>  (usb0): exported as /org/freedesktop/Hal/devices/net_02_12_13_14_15_22 
Oct 13 22:22:45 terra NetworkManager: <info>  (usb0): device state change: 1 -> 2 
Oct 13 22:22:45 terra NetworkManager: <info>  (usb0): bringing up device. 
Oct 13 22:22:45 terra NetworkManager: <info>  (usb0): preparing device. 
Oct 13 22:22:45 terra NetworkManager: <info>  (usb0): deactivating device (reason: 2). 
Oct 13 22:22:45 terra NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Oct 13 22:22:45 terra NetworkManager: <info>  (usb0): carrier now ON (device state 2) 
Oct 13 22:22:45 terra NetworkManager: <info>  (usb0): device state change: 2 -> 3 
Oct 13 22:22:46 terra avahi-daemon[6331]: Registering new address record for fe80::12:13ff:fe14:1522 on usb0.*.
Oct 13 22:22:47 terra NetworkManager: <info>  (ttyACM0): ignoring due to lack of mobile broadband capabilties 
jonsmirl@terra:/etc/NetworkManager$ 
```

Card is up:
```
usb0      Link encap:Ethernet  HWaddr 02:12:13:14:15:22  
          inet6 addr: fe80::12:13ff:fe14:1522/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1280  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

But script hasn't run, it looks like this if the script runs.
```
usb0      Link encap:Ethernet  HWaddr 02:12:13:14:15:22  
          inet6 addr: aaaa::1/64 Scope:Global
          inet6 addr: fe80::12:13ff:fe14:1522/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1280  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by jonsmirl on 2009-10-14
I believe the answer to this is that I need an IPV6 aware NetworkManager. Hopefully it is in 9.10.

I switched over to manual ifup/down configuration.

---

