---
title: "Network Manager VPN Manual Configuration"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by dbloom810 on 2009-05-04
Hello,

I am using network manager to handle a Cisco VPN connection through VPNC. However, I cannot seem to get the connection to complete and get a new IP from my vpn host.

Through searching the net, I found this problem is related to the "local port" that vpnc reserves for the connection. By default, this port is set to 500.

I can change the port to 0 (random) in the vpnc .conf file, and use kvpnc to do the same. Those both work after I make the change. However, network manager does NOT have the option to change the local port.

Is there a way to manually edit the configuration file that Network Manager is using for vpnc connections?

I'd really like to use network manager becuse I have to connect to my VPN 10+ times a day, and it seems like the most convient way to do this.

If anyone has any ideas about how to tell network manager exactly what to do, please let me know.

---

