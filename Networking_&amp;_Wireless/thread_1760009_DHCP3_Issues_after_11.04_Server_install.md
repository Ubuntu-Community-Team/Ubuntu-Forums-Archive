---
title: "DHCP3 Issues after 11.04 Server install"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by picbits on 2011-05-16
Well there goes another hour of my life lol.

I've just comissioned an 11.04 server and was having issues with the DHCP server.

I did the customary sudo apt-get install dhcp3-server, copied the dhcpd.conf from my old server to the same location on the new server, tried to start up ics-dhcp-server and got the following error (copied and pasted for Goggle purposes)

```
May 16 16:04:21 pbhpx dhcpd: No subnet declaration for eth0 (192.168.1.222).
May 16 16:04:21 pbhpx dhcpd: ** Ignoring requests on eth0.  If this is not what
May 16 16:04:21 pbhpx dhcpd:    you want, please write a subnet declaration
May 16 16:04:21 pbhpx dhcpd:    in your dhcpd.conf file for the network segment
May 16 16:04:21 pbhpx dhcpd:    to which interface eth0 is attached. **
May 16 16:04:21 pbhpx dhcpd:
May 16 16:04:21 pbhpx dhcpd:
May 16 16:04:21 pbhpx dhcpd: Not configured to listen on any interfaces!
```

After checking my dhcpd.conf file I had the same issues. I then copied and pasted another dhcpd.conf file but same problem.

Then I moved the file to a temporary directory - same problem. 

Strange - it didn't appear to be reading the file at all - no complaints about the file being missing. 

Then it twigged - there must be another one somewhere.

My original dhcpd.conf file was located in /etc/dhcp3/dhcpd.conf while the newer ics-dhcp-server was reading the /etc/dhcp/dhcp.conf file.

I copied the file back into /etc/dhcp, restarted the ics-dhcp-server and everything is now fine and dandy.

Bit of a waffle but if it saves others a bit of time it was worth it :)

---

