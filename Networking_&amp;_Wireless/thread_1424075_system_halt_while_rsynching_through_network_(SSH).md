---
title: "system halt while rsynching through network (SSH)"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by 666f6f on 2010-03-07
Hello all,

The following post describes a problem I encountered while rsynching through network (SSH).

I have 2 Ubuntu Desktop 9.10 (Karmic Koala) installations, one on a Dell Latitude D630 and one on a custom build desktop with these signatures:

Linux custom-desktop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux
Linux dell-laptop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux

The Dell uses the nVIDIA and Broadcom STA prorietary drivers.

I was rsynching some folders from Dell Latitude (source) to the Desktop (target) when suddenly the laptop froze completely.

I noticed that "Num Lock, Caps Lock, and Scroll Lock" status was "Off, Blinking and Blinking" which, according to the manual, ["a possible modem failure has occurred"]("http://support.dell.com/support/edocs/systems/latd630/en/UG/trouble.htm#wp1311135").

The troubleshooting hint from the user's guide in combination with the proprietary Broadcom STA driver makes me believe something's wrong with the Broadcom STA driver.

The last event prior to freeze was at Mar 7, 16:58:26.

Mar  7 16:44:18 myrsinie-laptop dhclient: DHCPOFFER of 192.168.1.11 from 192.168.1.1
Mar  7 16:44:18 myrsinie-laptop dhclient: DHCPREQUEST of 192.168.1.11 on eth2 to 255.255.255.255 port 67
Mar  7 16:44:18 myrsinie-laptop dhclient: DHCPACK of 192.168.1.11 from 192.168.1.1
Mar  7 16:44:18 myrsinie-laptop avahi-daemon[693]: Joining mDNS multicast group on interface eth2.IPv4 with address 192.168.1.11.
Mar  7 16:44:18 myrsinie-laptop avahi-daemon[693]: New relevant interface eth2.IPv4 for mDNS.
Mar  7 16:44:18 myrsinie-laptop avahi-daemon[693]: Registering new address record for 192.168.1.11 on eth2.IPv4.
Mar  7 16:44:18 myrsinie-laptop dhclient: bound to 192.168.1.11 -- renewal in 35000 seconds.
Mar  7 16:54:30 myrsinie-laptop gnome-session[2446]: WARNING: Could not launch application 'nm-applet.desktop': Unable to start application: Failed to execute child process "nm-applet" (No such file or directory)
Mar  7 16:58:26 myrsinie-laptop kernel: [  891.510043] CE: hpet increasing min_delta_ns to 15000 nsec

Have anyone experienced anything similar?

Thank you,
666f6f

P.S. To the future reader: We come in piece..

---

