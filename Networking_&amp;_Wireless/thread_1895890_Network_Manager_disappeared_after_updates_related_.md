---
title: "Network Manager disappeared after updates related to DHCP"
date: 2011-12-15
forum: Networking &amp; Wireless
---

### Post by NBPX on 2011-12-15
After receiving two updates related to DHCP through the package manager and restart the system, the network manager disappeared.

I took a look at the history of the Package Manager and found the following information:

The updated packages are:
-isc-dhcp-client
-isc-dhcp-common

When I restarted the computer it was without network ...

The history says that the following packages have been removed immediately after above mentioned:
-ubuntuminimal
-networkmanager
-plasma-widget-networkmanager

But I not did request the removal of the latter three. They are removed at the same time as the two mentioned above.

What should I do now? Will I have to download them and install them manually off-line?


I'm using Kubuntu 64.

---

