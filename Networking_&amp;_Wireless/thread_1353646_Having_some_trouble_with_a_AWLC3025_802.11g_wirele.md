---
title: "Having some trouble with a AWLC3025 802.11g wireless card"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by JudgeFeyd on 2009-12-13
I am currently using Hardy on an older Compaq Armada e500 with this Airlink card. I have the Windows XP driver in ndiswrapper and I can see wireless networks and attempt to join. I am never able to have an IP address assigned to this computer when attempting to connect wirelessly. This is true whether the network is open or secure. I followed the advice on this thread, [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847), to no avail really. not to sure what the issue is, but here is the system log when I attempt to join a network.



Dec 12 22:11:23 ubuntu dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Dec 12 22:11:23 ubuntu avahi-daemon[4860]: Withdrawing address record for 192.168.1.6 on eth0.
Dec 12 22:11:23 ubuntu avahi-daemon[4860]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.6.
Dec 12 22:11:23 ubuntu avahi-daemon[4860]: Interface eth0.IPv4 no longer relevant for mDNS.
Dec 12 22:11:23 ubuntu kernel: [  256.827590] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Dec 12 22:11:23 ubuntu avahi-daemon[4860]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec 12 22:11:23 ubuntu avahi-daemon[4860]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.62.
Dec 12 22:11:23 ubuntu avahi-daemon[4860]: Withdrawing address record for 169.254.9.62 on wlan0.
Dec 12 22:11:23 ubuntu dhclient: receive_packet failed on wlan0: Network is down
Dec 12 22:11:23 ubuntu dhclient: There is already a pid file /var/run/dhclient.pid with pid 134519072
Dec 12 22:11:23 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.0.6
Dec 12 22:11:23 ubuntu dhclient: Copyright 2004-2007 Internet Systems Consortium.
Dec 12 22:11:23 ubuntu dhclient: All rights reserved.
Dec 12 22:11:23 ubuntu dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Dec 12 22:11:23 ubuntu dhclient: 
Dec 12 22:11:23 ubuntu dhclient: Listening on LPF/wlan0/00:e0:98:d8:56:a9
Dec 12 22:11:23 ubuntu dhclient: Sending on   LPF/wlan0/00:e0:98:d8:56:a9
Dec 12 22:11:23 ubuntu dhclient: Sending on   Socket/fallback
Dec 12 22:11:23 ubuntu avahi-daemon[4860]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.62.
Dec 12 22:11:23 ubuntu avahi-daemon[4860]: New relevant interface wlan0.IPv4 for mDNS.
Dec 12 22:11:23 ubuntu avahi-daemon[4860]: Registering new address record for 169.254.9.62 on wlan0.IPv4.
Dec 12 22:11:23 ubuntu avahi-autoipd(wlan0)[5500]: SIOCSIFFLAGS failed: Permission denied
Dec 12 22:11:23 ubuntu avahi-autoipd(wlan0)[5500]: Callout STOP, address 169.254.9.62 on interface wlan0
Dec 12 22:11:23 ubuntu avahi-daemon[4860]: Withdrawing address record for 169.254.9.62 on wlan0.
Dec 12 22:11:23 ubuntu avahi-daemon[4860]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.62.
Dec 12 22:11:23 ubuntu avahi-daemon[4860]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec 12 22:11:23 ubuntu avahi-autoipd(wlan0)[5501]: client: RTNETLINK answers: No such process
Dec 12 22:11:36 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Dec 12 22:11:42 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Dec 12 22:11:55 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Dec 12 22:12:00 ubuntu dhclient: There is already a pid file /var/run/dhclient.pid with pid 134519072
Dec 12 22:12:00 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.0.6
Dec 12 22:12:00 ubuntu dhclient: Copyright 2004-2007 Internet Systems Consortium.
Dec 12 22:12:00 ubuntu dhclient: All rights reserved.
Dec 12 22:12:00 ubuntu dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Dec 12 22:12:00 ubuntu dhclient: 
Dec 12 22:12:01 ubuntu dhclient: Listening on LPF/wlan0/00:e0:98:d8:56:a9
Dec 12 22:12:01 ubuntu dhclient: Sending on   LPF/wlan0/00:e0:98:d8:56:a9
Dec 12 22:12:01 ubuntu dhclient: Sending on   Socket/fallback
Dec 12 22:12:03 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Dec 12 22:12:05 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Dec 12 22:12:05 ubuntu ntpd[5592]: sendto(199.212.17.34) (fd=18): Invalid argument
Dec 12 22:12:08 ubuntu ntpd[5592]: sendto(91.189.94.4) (fd=18): Invalid argument
Dec 12 22:12:09 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Dec 12 22:12:17 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Dec 12 22:12:22 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Dec 12 22:12:31 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Dec 12 22:12:37 ubuntu dhclient: No DHCPOFFERS received.
Dec 12 22:12:37 ubuntu dhclient: No working leases in persistent database - sleeping.
Dec 12 22:12:37 ubuntu avahi-autoipd(wlan0)[6309]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Dec 12 22:12:37 ubuntu avahi-autoipd(wlan0)[6309]: Successfully called chroot().
Dec 12 22:12:37 ubuntu avahi-autoipd(wlan0)[6309]: Successfully dropped root privileges.
Dec 12 22:12:37 ubuntu avahi-autoipd(wlan0)[6309]: Starting with address 169.254.9.62
Dec 12 22:12:39 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Dec 12 22:12:42 ubuntu avahi-autoipd(wlan0)[6309]: Callout BIND, address 169.254.9.62 on interface wlan0
Dec 12 22:12:42 ubuntu avahi-daemon[4860]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.62.
Dec 12 22:12:42 ubuntu avahi-daemon[4860]: New relevant interface wlan0.IPv4 for mDNS.
Dec 12 22:12:42 ubuntu avahi-daemon[4860]: Registering new address record for 169.254.9.62 on wlan0.IPv4.
Dec 12 22:12:46 ubuntu avahi-autoipd(wlan0)[6309]: Successfully claimed IP address 169.254.9.62
Dec 12 22:13:00 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Dec 12 22:13:04 ubuntu dhclient: No DHCPOFFERS received.
Dec 12 22:13:04 ubuntu dhclient: No working leases in persistent database - sleeping.
Dec 12 22:13:09 ubuntu ntpd[5592]: sendto(199.212.17.34) (fd=18): Invalid argument



Thanks for any help :)

---

