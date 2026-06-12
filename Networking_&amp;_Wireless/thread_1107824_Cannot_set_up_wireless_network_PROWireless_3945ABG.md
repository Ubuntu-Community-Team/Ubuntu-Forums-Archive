---
title: "Cannot set up wireless network PRO/Wireless 3945ABG [Golan] Network Connection"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by ubantuwannabe on 2009-03-27
I've problems setting up a wireless network on ubuntu on my laptop which is nc4400.

with reference to [http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

sudo ifconfig [interface] down
sudo dhclient -r [interface]
sudo ifconfig [interface] up
sudo iwconfig [interface] essid “ESSID_IN_QUOTES”
sudo iwconfig [interface] mode Managed
sudo dhclient [interface]

I did the above 

sudo ifconfig [interface] down
sudo dhclient -r wmaster0


Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback

sudo ifconfig wmaster0 up
SIOCSIFFLAGS: Operation not supported

sudo iwconfig wmaster0 esside "lzone"
iwconfig: unknown command "esside"

chunhung@chunhung-laptop:~$ sudo iwconfig wmaster0 mode Managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wmaster0 ; Operation not supported.

chunhung@chunhung-laptop:~$ sudo dhclient wmaster0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: Operation not supported
SIOCSIFFLAGS: Operation not supported
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
receive_packet failed on wmaster0: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down

how should i resolve this?

thanks

---

### Post by chili555 on 2009-03-27
*wmaster0* is not your actual interface. It's a sort of dummy second address that the driver needs. It does nothing and should be ignored. Please run this command:```
ifconfig -a
```Look through the output and see if you don't have an interface called *wlan0* or *eth1.* Re-run the commands with the correct interface name.

---

