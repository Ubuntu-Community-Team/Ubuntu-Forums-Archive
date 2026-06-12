---
title: "Dlink DFE660 on Acer Travelmate 212TXV - no link"
date: 2006-05-21
forum: Networking &amp; Wireless
---

### Post by akadruid on 2006-05-21
Hi all,

I have an Acer Travelmate 212TXV laptop.  This model does not have ethernet as standard, so I have got a D-link DFE660 PCMCIA ethernet card for it, which I cannot get working.

When I plug it in, I can hear hard disk activity.  The light labelled '10/100' lights up on the network dongle, but not 'Half/Full' or 'Ln/Act'. In the 'Network Settings' dialog, an Ethernet Connection appears.  I set this to use DHCP, and when I click Activate, it says 'Activating interface eth0' and a scrollbar moves for around 1 min, the lights on my hub for the sockets that the laptop and ADSL modem/router are plugged into flash, and then the Ethernet Connection entry says 'The interface eth0 is active'.

That's as far as I get though.  I cannot ping the router (Network is unreachable), ifconfig shows eth0 but does not show an 'inet addr' for it, only 'inet 6 addr'.  If I change the connection to static IP address in network settings, it then shows an ip address in ifconfig, but I still cannot ping (destination host is unreachable).

I followed the 'wired troubleshooting' post at the top of this forum, but the first section failed for me.  I get:
```
akadruid@spitfire:~$ sudo mii-tool eth0
eth0: autonegotiation restarted, no link
```

---

### Post by akadruid on 2006-06-06
I spent a long time mucking around with this and eventually tried installing this under a dual boot copy of Windows XP, which failed as well, even with updated drivers.

I can only conclude that it must be dead or incompatible hardware.  Beyond my time or ability to solve.  It was cheap anyway, so I have give up.

---

