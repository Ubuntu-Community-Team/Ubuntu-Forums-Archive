---
title: "ISC-DHCP Multi Subnets"
date: 2012-11-20
forum: Networking &amp; Wireless
---

### Post by Rattlehead_ie on 2012-11-20
Hi guys.
Hopefully I can explain this well enough that someone can help me out. Below is the dhcp.conf contents. In it there are 2 x /16 networks ready to be serviced.
10.1.0.0/16
10.230.0.0/16

The Server has 1 eth port eth0 and I wish to be able to hand out the above below ranges based on where the request comes from.
In between the clients and the Server is a JunOS based switch with helper IP addressing being used. i.e its inputting into the packet where there request is coming from. The issue seems to be that the request reaches the server...from the correct gateway but the server response with the wrong subnet. See the syslogs also below.
Any help would be appreciated
```

max-lease-time 84440;
default-lease-time 14440;
ddns-update-style none;
log-facility local7;
shared-network Net {

subnet 10.230.0.0 netmask 255.255.0.0 {
range dynamic-bootp 10.230.0.1 10.230.31.254;
option subnet-mask 255.255.0.0;
option broadcast-address 10.230.255.255;
option domain-name "Wired-net";
option domain-name-servers 8.8.8.8,8.8.4.4;
option routers 10.230.255.254;
}

subnet 10.1.0.0 netmask 255.255.0.0 {
range dynamic-bootp 10.1.0.1 10.1.31.254;
option subnet-mask 255.255.0.0;
option broadcast-address 10.1.255.255;
option domain-name "Wireless-net";
option domain-name-servers 8.8.8.8,8.8.4.4;
option routers 10.1.255.254;
}
```

The logs
> 
Nov 20 16:37:01 agile-ProLiant-ML150-G2 dhcpd: DHCPDISCOVER from d4:be:d9:30:bd:5e (MURRAYG-PC) via **_10.230.255.254_**
Nov 20 16:37:01 agile-ProLiant-ML150-G2 dhcpd: DHCPOFFER on **10.1.0.1** to d4:be:d9:30:bd:5e (MURRAYG-PC) via **_10.230.255.254_**
Nov 20 16:37:33 agile-ProLiant-ML150-G2 dhcpd: DHCPDISCOVER from d4:be:d9:30:bd:5e (MURRAYG-PC) via 10.230.255.254
Nov 20 16:37:33 agile-ProLiant-ML150-G2 dhcpd: DHCPOFFER on 10.1.0.1 to d4:be:d9:30:bd:5e (MURRAYG-PC) via 10.230.255.254
Nov 20 16:37:37 agile-ProLiant-ML150-G2 dhcpd: DHCPDISCOVER from d4:be:d9:30:bd:5e (MURRAYG-PC) via 10.230.255.254
Nov 20 16:37:37 agile-ProLiant-ML150-G2 dhcpd: DHCPOFFER on 10.1.0.1 to d4:be:d9:30:bd:5e (MURRAYG-PC) via 10.230.255.254
Nov 20 16:37:44 agile-ProLiant-ML150-G2 dhcpd: DHCPDISCOVER from d4:be:d9:30:bd:5e (MURRAYG-PC) via 10.230.255.254
Nov 20 16:37:44 agile-ProLiant-ML150-G2 dhcpd: DHCPOFFER on 10.1.0.1 to d4:be:d9:30:bd:5e (MURRAYG-PC) via 10.230.255.254


As above, you can see I've highlighted where the request has come from, then the response from DHCP with the wrong subnet.

Again any help would be great.

/Rattle

---

### Post by Rattlehead_ie on 2012-11-20
OK.
Solved. I was being stupid an believing JunOS over the DHCP. The packet is infact BOOTP that the JunOS unit sends out so once I changed the ranges to

> range dynamic-bootp
they worked.

---

### Post by Rattlehead_ie on 2012-11-20
Looks like I was a little premature with my Solved 

The setup is as above nothing has changed except the
```
range dynamic-bootp
```

The issue is still although one client will receive the right IP subnet from the 10.230.x.x (Wired) range. When another client tries to access the 10.1.x.x range (wireless) the dhcp server see's the DHCPrequest come from the right gateway but does not send the correct DHCP IP address back. still picking that of the wired network.

---

