---
title: "3G connection painfully unreliable"
date: 2012-09-10
forum: Networking &amp; Wireless
---

### Post by hartz on 2012-09-10
Most of the time I just use WiFi or Wired Ethernet but ocassionally I have to connect while "on the road", like right now.

My 3G modem used to work well most of the time.  But it just disconnects intermittendly, sometimes after three minutes, sometimes after 30.

Even more frustratingly, when it disconnects, it will not conenct again until I reboot.  I am sure it was better on previous releases - right now I am using KUbuntu 12.04, (last fully updated less than a week ago)

Below is the "event" when the connection gets terminated.
```

Sep  9 13:17:01 johan-Thinkpad CRON[3096]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  9 13:24:55 johan-Thinkpad dbus[897]: [system] Activating service name='org.kubuntu.qaptworker' (using servicehelper)
Sep  9 13:24:56 johan-Thinkpad dbus[897]: [system] Successfully activated service 'org.kubuntu.qaptworker'
Sep  9 13:24:56 johan-Thinkpad dbus[897]: [system] Activating service name='org.debian.AptXapianIndex' (using servicehelper)
Sep  9 13:24:56 johan-Thinkpad dbus[897]: [system] Successfully activated service 'org.debian.AptXapianIndex'
[COLOR="Red"]Sep  9 13:34:06 johan-Thinkpad pppd[2704]: Modem hangup[/COLOR]
Sep  9 13:34:06 johan-Thinkpad pppd[2704]: Connect time 19.3 minutes.
Sep  9 13:34:06 johan-Thinkpad pppd[2704]: Sent 617836 bytes, received 4729019 bytes.
Sep  9 13:34:06 johan-Thinkpad kernel: [ 1365.392148] usb 5-2: USB disconnect, device number 3
Sep  9 13:34:06 johan-Thinkpad kernel: [ 1365.393646] option: option_instat_callback: error -108
Sep  9 13:34:06 johan-Thinkpad kernel: [ 1365.400207] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Sep  9 13:34:06 johan-Thinkpad kernel: [ 1365.400241] option 5-2:1.0: device disconnected
Sep  9 13:34:06 johan-Thinkpad kernel: [ 1365.400576] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Sep  9 13:34:06 johan-Thinkpad kernel: [ 1365.400623] option 5-2:1.1: device disconnected
Sep  9 13:34:06 johan-Thinkpad pppd[2704]: Connection terminated.
Sep  9 13:34:06 johan-Thinkpad modem-manager[920]: <info>  (ttyUSB0) closing serial port...
Sep  9 13:34:06 johan-Thinkpad modem-manager[920]: <info>  (ttyUSB0) serial port closed
Sep  9 13:34:06 johan-Thinkpad NetworkManager[948]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep  9 13:34:06 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): now unmanaged
Sep  9 13:34:06 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
Sep  9 13:34:06 johan-Thinkpad modem-manager[920]: <info>  (tty/ttyUSB0): released by modem /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-2
Sep  9 13:34:06 johan-Thinkpad modem-manager[920]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connected -> disabled)
Sep  9 13:34:06 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): deactivating device (reason 'removed') [36]
Sep  9 13:34:06 johan-Thinkpad NetworkManager[948]: <warn> could not read ppp stats: No such device
Sep  9 13:34:06 johan-Thinkpad NetworkManager[948]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Sep  9 13:34:06 johan-Thinkpad NetworkManager[948]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Sep  9 13:34:06 johan-Thinkpad dnsmasq[2763]: exiting on receipt of SIGTERM
Sep  9 13:34:06 johan-Thinkpad NetworkManager[948]: <info> DNS: starting dnsmasq...
Sep  9 13:34:06 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): writing resolv.conf to /sbin/resolvconf
Sep  9 13:34:06 johan-Thinkpad dnsmasq[5031]: started, version 2.59 cache disabled
Sep  9 13:34:06 johan-Thinkpad dnsmasq[5031]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Sep  9 13:34:06 johan-Thinkpad dnsmasq[5031]: warning: no upstream servers configured
Sep  9 13:34:06 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): cleaning up...
Sep  9 13:34:06 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): taking down device.
Sep  9 13:34:06 johan-Thinkpad NetworkManager[948]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Sep  9 13:34:06 johan-Thinkpad dbus[897]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Sep  9 13:34:06 johan-Thinkpad dbus[897]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Sep  9 13:34:08 johan-Thinkpad pppd[2704]: Exit.
Sep  9 13:34:16 johan-Thinkpad kernel: [ 1375.872157] usb 5-2: new full-speed USB device number 4 using uhci_hcd
Sep  9 13:34:16 johan-Thinkpad mtp-probe: checking bus 5, device 4: "/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-2"
Sep  9 13:34:16 johan-Thinkpad kernel: [ 1376.094453] option 5-2:1.0: GSM modem (1-port) converter detected
Sep  9 13:34:16 johan-Thinkpad kernel: [ 1376.094665] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB0
Sep  9 13:34:16 johan-Thinkpad kernel: [ 1376.096449] option 5-2:1.1: GSM modem (1-port) converter detected
Sep  9 13:34:16 johan-Thinkpad kernel: [ 1376.096724] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB1
Sep  9 13:34:16 johan-Thinkpad kernel: [ 1376.097314] scsi10 : usb-storage 5-2:1.2
Sep  9 13:34:16 johan-Thinkpad mtp-probe: bus: 5, device: 4 was not an MTP device
Sep  9 13:34:16 johan-Thinkpad modem-manager[920]: <info>  (ttyUSB0) opening serial port...
Sep  9 13:34:17 johan-Thinkpad modem-manager[920]: <info>  (ttyUSB0) closing serial port...
Sep  9 13:34:17 johan-Thinkpad modem-manager[920]: <info>  (ttyUSB0) serial port closed
Sep  9 13:34:17 johan-Thinkpad modem-manager[920]: <info>  (ttyUSB0) opening serial port...
Sep  9 13:34:17 johan-Thinkpad modem-manager[920]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-2 claimed port ttyUSB0
Sep  9 13:34:17 johan-Thinkpad kernel: [ 1377.100216] scsi 10:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Sep  9 13:34:17 johan-Thinkpad kernel: [ 1377.117210] sr1: scsi-1 drive
Sep  9 13:34:17 johan-Thinkpad kernel: [ 1377.118718] sr 10:0:0:0: Attached scsi CD-ROM sr1
Sep  9 13:34:17 johan-Thinkpad kernel: [ 1377.119804] sr 10:0:0:0: Attached scsi generic sg2 type 5
Sep  9 13:34:18 johan-Thinkpad modem-manager[920]: <info>  (ttyUSB0) closing serial port...
Sep  9 13:34:18 johan-Thinkpad modem-manager[920]: <info>  (ttyUSB0) serial port closed
Sep  9 13:34:19 johan-Thinkpad modem-manager[920]: <info>  (ttyUSB1) opening serial port...
Sep  9 13:34:20 johan-Thinkpad modem-manager[920]: <info>  (ttyUSB1) closing serial port...
Sep  9 13:34:20 johan-Thinkpad modem-manager[920]: <info>  (ttyUSB1) serial port closed
Sep  9 13:34:20 johan-Thinkpad modem-manager[920]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-2 claimed port ttyUSB1
Sep  9 13:34:20 johan-Thinkpad NetworkManager[948]: <warn> (ttyUSB0): failed to look up interface index
Sep  9 13:34:20 johan-Thinkpad NetworkManager[948]: <info> WWAN now disabled by management service
Sep  9 13:34:20 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): new GSM/UMTS device (driver: 'option1' ifindex: 0)
Sep  9 13:34:20 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): exported as /org/freedesktop/NetworkManager/Devices/3
Sep  9 13:34:20 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): now managed
Sep  9 13:34:20 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Sep  9 13:34:20 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): deactivating device (reason 'managed') [2]
Sep  9 13:34:20 johan-Thinkpad NetworkManager[948]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Sep  9 13:34:20 johan-Thinkpad NetworkManager[948]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Sep  9 13:34:20 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]

Sep  9 13:36:42 johan-Thinkpad kernel: [ 1521.880181] usb 5-2: USB disconnect, device number 4
Sep  9 13:36:42 johan-Thinkpad kernel: [ 1521.882174] option: option_instat_callback: error -108
Sep  9 13:36:42 johan-Thinkpad kernel: [ 1521.882503] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Sep  9 13:36:42 johan-Thinkpad kernel: [ 1521.882549] option 5-2:1.0: device disconnected
Sep  9 13:36:42 johan-Thinkpad kernel: [ 1521.883916] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Sep  9 13:36:42 johan-Thinkpad kernel: [ 1521.883958] option 5-2:1.1: device disconnected
Sep  9 13:36:42 johan-Thinkpad modem-manager[920]: <info>  (tty/ttyUSB0): released by modem /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-2
Sep  9 13:36:42 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): now unmanaged
Sep  9 13:36:42 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): device state change: disconnected -> unmanaged (reason 'removed') [30 10 36]
Sep  9 13:36:42 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): cleaning up...
Sep  9 13:36:42 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): taking down device.
Sep  9 13:36:42 johan-Thinkpad NetworkManager[948]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Sep  9 13:36:42 johan-Thinkpad NetworkManager[948]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)

```


And this is what I see if I try to connect again.
```

Sep  9 13:40:19 johan-Thinkpad NetworkManager[948]: <info> Activation (ttyUSB0) starting connection 'Vodacom'
Sep  9 13:40:19 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep  9 13:40:19 johan-Thinkpad NetworkManager[948]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Sep  9 13:40:19 johan-Thinkpad NetworkManager[948]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Sep  9 13:40:19 johan-Thinkpad NetworkManager[948]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Sep  9 13:40:19 johan-Thinkpad modem-manager[920]: <info>  (ttyUSB0) opening serial port...
Sep  9 13:40:19 johan-Thinkpad modem-manager[920]: <info>  Modem /org/freedesktop/ModemManager/Modems/2: state changed (disabled -> enabling)
Sep  9 13:40:19 johan-Thinkpad modem-manager[920]: <info>  (ttyUSB1) opening serial port...
Sep  9 13:40:19 johan-Thinkpad modem-manager[920]: <info>  (ttyUSB0): using text mode for SMS
Sep  9 13:40:19 johan-Thinkpad modem-manager[920]: <info>  Modem /org/freedesktop/ModemManager/Modems/2: state changed (enabling -> enabled)
Sep  9 13:40:19 johan-Thinkpad NetworkManager[948]: <info> WWAN now enabled by management service
Sep  9 13:40:19 johan-Thinkpad modem-manager[920]: <info>  Modem /org/freedesktop/ModemManager/Modems/2: state changed (enabled -> registered)
Sep  9 13:40:58 johan-Thinkpad NetworkManager[948]: <warn> GSM connection failed: (32) Serial command timed out
Sep  9 13:40:58 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): device state change: prepare -> failed (reason 'unknown') [40 120 1]
Sep  9 13:40:58 johan-Thinkpad NetworkManager[948]: <warn> Activation (ttyUSB0) failed.
Sep  9 13:40:58 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Sep  9 13:40:58 johan-Thinkpad NetworkManager[948]: <info> (ttyUSB0): deactivating device (reason 'none') [0]
Sep  9 13:40:58 johan-Thinkpad NetworkManager[948]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Sep  9 13:40:58 johan-Thinkpad NetworkManager[948]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed

```

I get the same even if I re-plug the 3G modem.  Only a reboot allws me to reconnect (for a few minutes)

Also it appears that f I reboot with the 3G modem conencted, I can't connect at all.

---

### Post by hartz on 2012-09-11
Sigh... my problems seems to be too elusive.

I noticed mention in many forum posts about something called sakis3g so I downloaded it and this morning I tested it.

1. rebooted
2. connected normally (using KDE connection manager)
3. browsed for a while untill connection failed.
4. tried several times to re-connect, but it just timed out.  This includes moving the 3G USB modem to other USB ports.
5. Tried sakis3g script.  It said that it had connected but the LED on the modem went stable green, which indicates an EDGE only connection.  I did get an IP address but could not actually talk.  I think address resolution worked, but nothing else.
6. I disconnected and re-connected, but chose the "unlimited" option in stead of "internet" for APN.  This time I got a steady BLUE light on the modem and it worked well for a few minutes (I was able to browse, send email, etc)
7. Then the modem disconnected and would not reconnect no matter which APN option I selected (sakis3G got the modem to show an EDGE conenction, KDE network manager just timed out each time)

So ... still no stable connection.  At this point I would be happy if I could just reliably re-connect after a connection failure.

---

### Post by p1977p on 2012-10-14
I have a solution to this problem. Please see my post

[http://ubuntuforums.org/showthread.php?p=12294889](http://ubuntuforums.org/showthread.php?p=12294889)

---

