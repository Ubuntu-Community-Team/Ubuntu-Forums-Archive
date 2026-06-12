---
title: "Can only get IP address by booting windows first"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by BetterSense on 2008-12-31
I have a DSL modem behind a Linksys wrt54g router. If I boot ubuntu, it never gets an IP address or anything. If I boot Vista, the network works. So then if I switch back, it works in ubuntu, like it is now. It has repeated this behavior several times. Vista must be doing some kind of configurating that 'lasts' long enough to boot back into linux and have it work. Any ideas what is going on?

---

### Post by steeleyuk on 2008-12-31
Sounds like Ubuntu isn't issuing a DHCP request. If the network connection is working now, that means your drivers and settings seem to be fine. Have you tried pinging the router immediately after booting Ubuntu (without going into Windows first)?

---

### Post by BetterSense on 2008-12-31
Ok I booted straight to ubuntu after leaving the computer off for an hour. Networking is not working, there is no IP address in the 'connection information' bit of nm-applet, it's all zeros where the IP should be.

I tried running ping 192.168.1.1 and it fails, destination host unreachable. I cannot navigate to the router's firmware page with firefox either. 

So what does all this mean? This computer i'm typing on right now is a separate computer in the same room, running freshly installed Hardy Heron, and it has had no problems with internet. It's only the HP pavillion that I setup dual-boot on that is having the trouble.

---

### Post by steeleyuk on 2008-12-31
OK, we can try to issue the DHCP command manually. Open a terminal and enter:
sudo dhclient <interface>

For example, mine was: sudo dhclient wlan0, and I got the output:
```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0e:2e:c5:36:97
Sending on   LPF/wlan0/00:0e:2e:c5:36:97
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.0.2 from 192.168.0.1
DHCPREQUEST of 192.168.0.2 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.2 from 192.168.0.1
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
resolvconf: Error: /etc/resolv.conf must be a symlink
bound to 192.168.0.2 -- renewal in 38948 seconds.
```

This should ask the router to give you a new IP. If this isn't the problem then I'd suspect its a driver issue at startup or a bad update/config file, which is probably a lot more difficult to track down.

---

