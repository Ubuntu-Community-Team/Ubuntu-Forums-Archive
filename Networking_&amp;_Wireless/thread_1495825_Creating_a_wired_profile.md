---
title: "Creating a wired profile"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by johnathanamber on 2010-05-28
Hello everyone,

I am trying to make a wired profile for my laptop at work.

I have a specific gateway that I want all traffic to go through but I need everything else to be DHCP.

What I've done was:
R/C Network Manager Applet > Edit Connections
Under 'Wired' > Add
Assigned a name
Clicked the 'IPv4 Settings'
Method = 'Automatic DHCP'
Clicked on 'Routes'
Added the following route:
Address  Netmask  Gateway          Metric
0.0.0.0  0.0.0.0  xxx.xxx.xxx.xxx  1

Also checked: 'Ignore automatically obtained routes'

Click 'OK' > 'Apply'

If I go back into the same profile > IPv4 Settings > Routes

The route is not there and theignore option is cleared (not checked).

Any way I can do this?

Thank you,
Johnathan

---

