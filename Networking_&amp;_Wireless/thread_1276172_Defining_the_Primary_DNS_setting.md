---
title: "Defining the Primary DNS setting"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by DarkMage2303 on 2009-09-26
How can I change the DNS settings that Ubuntu 8.10 uses by default?

At the moment, I have my DNS settings set to OpenDNS' name servers, 208.67.222.222, 208.67.220.220 but my internet doesn't work.

---

### Post by spd106 on 2009-09-27
The Ubuntu system uses the settings in the /etc/resolv.conf file for DNS. 

You shouldn't edit this by hand as it'll just be overwritten by Network Manager. Instead open the Network Connections program and change the IPv4 settings to only get the addresses via DHCP and then add your DNS IP addresses as a comma separated list.

Once you finished these changes should now be reflected in the resolv.conf file.

---

### Post by Iowan on 2009-09-27
_IF_ you use DHCP, you can edit the "prepend" line in */etc/dhcp3/dhclient.conf* to put your preferred nameservers at the top of the list.

---

