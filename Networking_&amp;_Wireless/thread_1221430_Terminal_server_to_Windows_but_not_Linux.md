---
title: "Terminal server to Windows but not Linux"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by DenysT on 2009-07-23
This seems strange but I can use terminal server to remotely connect to the one XP machine on the network but I can't use it on the Linux PC to connect to the other Linux PC. I get an error: getaddrinfo Name or service not known. Both are Ubuntu 9.04. I can use all other network shares on all machines in all directions, ie Windows to Linux, Linux to Windows with no problems.

If I try to browse network computers from XP remote connection it tells me there are no terminal servers on the network but I have set up both Linux machines to be terminal servers with the results IP address,machinename.local. However XP will not accept anything but IP address and tells me no such machine exists.

All three machines are through a Belkin router, hardwired and show up in the DHCP client listing.

So my question is: Why can I connect remotely to XP from Linux but not to Linux from any machine, Linux or Windows?

---

### Post by DenysT on 2009-07-25
Update: I got rid of the getaddrinfo error by adjusting a setting on the router but I still can't remotely connect to any Ubuntu 9.04 PC. Now I just get the error "Unable to connect." I can use remote window viewer just fine, I can browse all machines on the network and bring up their shares, I can print to shared printers on the network.

Sometimes when I setup the PC for remote connections I get a foreign address like 64.188.212.217 instead of a local address for the PC like 192.168.2.5. What is going on with that?

---

