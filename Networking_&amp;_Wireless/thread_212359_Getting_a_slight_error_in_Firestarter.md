---
title: "Getting a slight error in Firestarter"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by Thiesen on 2006-07-09
This is what happens when I run Firestarter in Ubuntu Dapper (Firestarter 1.0.3-1.1ubuntu4 aka version 1.0.3):

```

user@computername:~$ sudo firestarter

*ALSA errormessages removed since not needed*
iptables v1.3.3: host/network `192.168.0.10-192.168.0.254' not found
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.3: host/network `192.168.0.10-192.168.0.254' not found
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.3: host/network `192.168.0.10-192.168.0.254' not found
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.3: host/network `192.168.0.10-192.168.0.254' not found
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.3: host/network `192.168.0.10-192.168.0.254' not found
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.3: host/network `192.168.0.10-192.168.0.254' not found
Try `iptables -h' or 'iptables --help' for more information.
Firewall started
Failed to start DHCP server
``` 

The last "Failed to start DHCP Server" is total bs since I know it is working just fine.

The thing is that I get a popup telling me that "Failed to start the firewall, An unknown error occured. *Some error text in Swedish that basically tells me to check my network configuration*"

If only I knew which of the logfiles to check in /var/log I could write what it says but I don't know which of them to check.

I have been trying both dhcpd3 and the other dhcpd server and they both give the same result.

Other than that Firestarter runs just fine and I can configure all the firewall rules I need.

If you need more information just tell me what you need and I will try to provide that for you.

---

### Post by peaceburn on 2006-09-14
Uhm, not sure as this is quite an old thread ... but I was playing with firestarter, and was trying to setup a nat with dhcp ... it was failing, until I did 

root@bastard:/usr/sbin# ln dhcpd3 dhcpd

so this may be the case in your situation, or someone else experiencing such problem.

p.s. this is with firestarter 1.0.3-1.1u

---

### Post by paulirotta on 2007-04-01
Adding this link (and installing the DHCP server) solved the problem for me also. Thanks!

---

