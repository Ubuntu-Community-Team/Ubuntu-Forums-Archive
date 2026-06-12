---
title: "Disconnecting USB Modem within every 2 minutes"
date: 2012-07-21
forum: Networking &amp; Wireless
---

### Post by Prakhar Mishra on 2012-07-21
I am using micromax usb modem with Idea network as ISP in India. I am using Ubuntu 12.04. I have to perform a modprobe to detect my device as USB Modem. Moreover, it takes around a minute for NetworkManager to detect and show Mobile Broadbands available. 

When I connect to the internet, it gets disconnected almost every time within 1-2 min. If I am lucky enough, the connection survives and last long. However, it happens only once in a while. How should I deal with it?

Here is the output of /var/log/syslog
-------------------------------------------------------

Jul 21 22:08:54 prakhar-PC pppd[11164]: LCP terminated by peer
Jul 21 22:08:54 prakhar-PC pppd[11164]: Connect time 1.4 minutes.
Jul 21 22:08:54 prakhar-PC pppd[11164]: Sent 11760 bytes, received 71575 bytes.
Jul 21 22:08:54 prakhar-PC pppd[11164]: Modem hangup
Jul 21 22:08:54 prakhar-PC pppd[11164]: Connection terminated.
Jul 21 22:08:54 prakhar-PC avahi-daemon[1138]: Withdrawing workstation service for ppp0.
Jul 21 22:08:54 prakhar-PC modem-manager[1028]: <info>  (ttyUSB3) closing serial port...
Jul 21 22:08:54 prakhar-PC modem-manager[1028]: <info>  (ttyUSB3) serial port closed
Jul 21 22:08:54 prakhar-PC NetworkManager[1101]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul 21 22:08:54 prakhar-PC NetworkManager[1101]: <info> (ttyUSB3): now unmanaged
Jul 21 22:08:54 prakhar-PC NetworkManager[1101]: <info> (ttyUSB3): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
Jul 21 22:08:54 prakhar-PC NetworkManager[1101]: <info> (ttyUSB3): deactivating device (reason 'removed') [36]
Jul 21 22:08:54 prakhar-PC NetworkManager[1101]: <warn> could not read ppp stats: No such device
Jul 21 22:08:54 prakhar-PC NetworkManager[1101]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Jul 21 22:08:54 prakhar-PC NetworkManager[1101]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Jul 21 22:08:54 prakhar-PC dnsmasq[11210]: exiting on receipt of SIGTERM
Jul 21 22:08:54 prakhar-PC NetworkManager[1101]: <info> DNS: starting dnsmasq...
Jul 21 22:08:54 prakhar-PC NetworkManager[1101]: <info> (ttyUSB3): writing resolv.conf to /sbin/resolvconf
Jul 21 22:08:54 prakhar-PC dnsmasq[11368]: started, version 2.59 cache disabled
Jul 21 22:08:54 prakhar-PC dnsmasq[11368]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jul 21 22:08:54 prakhar-PC dnsmasq[11368]: warning: no upstream servers configured
Jul 21 22:08:54 prakhar-PC NetworkManager[1101]: <info> (ttyUSB3): cleaning up...
Jul 21 22:08:54 prakhar-PC NetworkManager[1101]: <info> (ttyUSB3): taking down device.
Jul 21 22:08:54 prakhar-PC NetworkManager[1101]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Jul 21 22:08:54 prakhar-PC modem-manager[1028]: <info>  Modem /org/freedesktop/ModemManager/Modems/2: state changed (connected -> disconnecting)
Jul 21 22:08:54 prakhar-PC dbus[985]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul 21 22:08:54 prakhar-PC modem-manager[1028]: <info>  Modem /org/freedesktop/ModemManager/Modems/2: state changed (disconnecting -> connected)
Jul 21 22:08:54 prakhar-PC NetworkManager[1101]: <info> disconnect failed: (32) The serial port is not open.
Jul 21 22:08:54 prakhar-PC dbus[985]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 21 22:08:56 prakhar-PC pppd[11164]: Exit.

---

### Post by p1977p on 2012-10-14
Please post the output of : (type in terminal)

dmesg |grep tty

Also take a look at my post:

[http://ubuntuforums.org/showthread.php?p=12294889](http://ubuntuforums.org/showthread.php?p=12294889)

---

