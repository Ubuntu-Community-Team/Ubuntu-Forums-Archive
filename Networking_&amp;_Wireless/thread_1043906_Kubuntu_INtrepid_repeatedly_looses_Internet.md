---
title: "Kubuntu INtrepid repeatedly looses Internet"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by mibadt on 2009-01-19
Hi,
Since yesterday, my Kubuntu Intrepid began "loosing" it's Internet connection with minutes after start, and repeated the same behavior and rebooting.
Initially I booted Knoppix and verified that my Internet infrastructure was steady as rock (which it was and maintained the Internet connection steady).
I've checked the syslog file and found that:
1. Initially after boot my Internet was working.
2. Less than a minute afterwards, the following lines appeared in my logfile, and, as suspected, at that stage my Internet connection was gone.

My network configuration:
1. Kubuntu Intrepid (fully updated working fine ill the day before yesterday), connected via eth0 (DHCP enabled) on a 10.0.0.x LAN to an ADSL modem/router.
2. No other network interfaces in that computer.

Whenever I loose Internet I access the ADSL router (via http interface) and verify that it got disconnected. When I reboot the router (via same interface, or via power down) I temporarily regain Internet only o loose it again as above.


Am I correct guessing some "dialer" tries to connect?
How can I get back my normal steady Internet connection.

----------the "suspected" log file tail--------
Jan 19 06:44:59 Miki-Desktop kernel: [  146.109614] ppdev0: registered pardevice
Jan 19 06:44:59 Miki-Desktop kernel: [  146.156179] ppdev0: unregistered pardevice
Jan 19 06:45:00 Miki-Desktop kernel: [  146.844301] ppdev0: registered pardevice
Jan 19 06:45:00 Miki-Desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jan 19 06:45:00 Miki-Desktop kernel: [  146.892296] ppdev0: unregistered pardevice
Jan 19 06:45:00 Miki-Desktop kernel: [  146.938469] ppdev0: registered pardevice
Jan 19 06:45:00 Miki-Desktop hp: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jan 19 06:45:00 Miki-Desktop kernel: [  146.988495] ppdev0: unregistered pardevice
--------------end-----------------


Best Regards,

Michael Badt

---

