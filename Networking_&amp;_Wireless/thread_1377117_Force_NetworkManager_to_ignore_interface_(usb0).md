---
title: "Force NetworkManager to ignore interface (usb0)"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by naught101 on 2010-01-09
I bought a Freerunner the other day (opensource phone/pda), and I'm trying to get usb networking going on my PC at the same time as wireless, so that I can connect to the internet from the Freerunner, but NetworkManager doesn't play nicely.

So:
[LIST]
[*]usb networking is working fine, I can connect to the freerunner with ssh, etc. Have to connect using /etc/network/interfaces and ifup usb0, which is fine.
[*]Wireless on the PC is working fine.
[*]When both networks are up, I can connect to the 'net from the freerunner fine using IP forwarding.
[/LIST]

But the connection only lasts for a few seconds, because netowrkmanager continually screws with the usb0 interface, like this:
```
naught101@naught-laptop:4AR$ tail -f /var/log/syslog
Jan 10 14:39:22 naught-laptop kernel: [39247.836210] usb 4-1: new full speed USB device using uhci_hcd and address 12
Jan 10 14:39:22 naught-laptop kernel: [39248.051440] usb 4-1: configuration #1 chosen from 2 choices
Jan 10 14:39:22 naught-laptop kernel: [39248.075354] usb0: register 'cdc_ether' at usb-0000:00:1d.2-1, CDC Ethernet Device, 0a:97:4f:52:31:3d
Jan 10 14:39:22 naught-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/net/usb0, iface: usb0)
Jan 10 14:39:22 naught-laptop NetworkManager:    SCPluginIfupdown: locking wired connection setting
Jan 10 14:39:22 naught-laptop NetworkManager:    Ifupdown: get unmanaged devices count: 1
Jan 10 14:39:22 naught-laptop NetworkManager: <info>  (usb0): carrier is OFF
Jan 10 14:39:22 naught-laptop NetworkManager: <info>  (usb0): new Ethernet device (driver: 'cdc_ether')
Jan 10 14:39:22 naught-laptop NetworkManager: <info>  (usb0): exported as /org/freedesktop/NetworkManager/Devices/3
Jan 10 14:39:59 naught-laptop wpa_supplicant[1116]: CTRL-EVENT-SCAN-RESULTS
Jan 10 14:40:54 naught-laptop avahi-daemon[839]: Joining mDNS multicast group on interface usb0.IPv4 with address 192.168.0.200.
Jan 10 14:40:54 naught-laptop avahi-daemon[839]: IP_ADD_MEMBERSHIP failed: No buffer space available
Jan 10 14:40:54 naught-laptop avahi-daemon[839]: Registering new address record for 192.168.0.200 on usb0.IPv4.
Jan 10 14:40:54 naught-laptop NetworkManager: <info>  (usb0): carrier now ON (device state 1)
Jan 10 14:40:54 naught-laptop avahi-daemon[839]: Joining mDNS multicast group on interface usb0.IPv4 with address 192.168.0.200.
Jan 10 14:40:54 naught-laptop avahi-daemon[839]: IP_ADD_MEMBERSHIP failed: No buffer space available
Jan 10 14:40:54 naught-laptop NetworkManager: <info>  (usb0): carrier now OFF (device state 1)
Jan 10 14:40:55 naught-laptop avahi-daemon[839]: Registering new address record for fe80::200:22ff:fe55:bb00 on usb0.*.
Jan 10 14:41:04 naught-laptop kernel: [39350.244031] usb0: no IPv6 routers present
Jan 10 14:41:15 naught-laptop ntpdate[12534]: no server suitable for synchronization found
Jan 10 14:41:21 naught-laptop avahi-daemon[839]: Joining mDNS multicast group on interface usb0.IPv4 with address 192.168.0.200.
Jan 10 14:41:21 naught-laptop avahi-daemon[839]: IP_ADD_MEMBERSHIP failed: No buffer space available
Jan 10 14:41:21 naught-laptop NetworkManager: <info>  (usb0): carrier now ON (device state 1)

```

Note especially the lines:
NetworkManager: <info>  (usb0): carrier now OFF (device state 1)
NetworkManager: <info>  (usb0): carrier now ON (device state 1)

After "carrier now OFF", the connection becomes unresponsive, after "ON", if comes back up. The cycle happens about once a minute, and is OFF most of the time.

There's some more background here: [http://wiki.openmoko.org/wiki/USB_Networking#Debian.2C_Ubuntu_and_others](http://wiki.openmoko.org/wiki/USB_Networking#Debian.2C_Ubuntu_and_others)

I've tried setting up a manual-ip wired connection in knetworkmanager (and in nm-applet). It seemed to work for a while, but now it's doing the same thing again.

Basically, I'm wondering if there's a way to get NetworkManager to completely ignore the usb0 interface? Or at least get it to stop trying to restart it every 60 seconds?

---

### Post by naught101 on 2010-01-10
hrm... I think this may have been caused by the wireless attempting to connect on the freerunner, and disabling the usb network interface.

Never-the-less, it'd be nice to be able to blacklist interfaces from NetworkManager..

---

