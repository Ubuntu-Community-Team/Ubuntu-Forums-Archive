---
title: "no internet connection even if dhcp works"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by go4usg50 on 2012-10-24
hello.

i need some help in network settings.

i manage about 25 pc's. some uses windows 7 others lubuntu 12.04 desktop. all off them get there network settings by dhcp from a zyxel zywall usg 50.

our isp has changed the configuration and hardware in order to have faster download and upload speeds. the isp recommended to protect our lan with the zywall usg 50.
because i doesn't now all the options the zywall has, i used the configuration assistant in order to set the wan ip, the gateway ip and both nameservers (opendns).

i tested the settings with my laptop (lenovo x200s, lubuntu 12.04 desktop). i attached the lenovo with a lan cable to the port lan1 of the zywall and i got a working internet connenction (zywall dhcp server; lenovo dhcp client).

after that i connect the lan1 port of the zywall with a netgear switch in order to conncet about 25 pc's.

now i have a strange effect: all pc's using windows 7 could connect to the internet. but all pc's using lubuntu 12.04 desktop couldn't. 
but when i check the dhcp settings of a lubuntu pc evwerthing seems ok (ip, gateway (zywall), nameserver (zywall)). if i replace the linux pc with a windows pc, i get a working internet connection.

behind the zywall there are two ausu routers with tomato usb firmware. both router get there wan configuration from the zywall and everthing seems ok. but there is no internet.

what could be the reason that windows 7 works and lubuntu dosen't work.

any hint is welcome.

kind regards, go4usg50

---

### Post by ahallubuntu on 2012-10-24
Try to eliminate each possibility one at a time.

Can you plug one of the Lubuntu PCs that does not get internet from the Netgear switch directly into a router port instead?  (If that works, then it's the switch; if that has the same problem, the switch isn't the problem.)

If you are plugged into the switch and can't get to the internet (but you seem to be on the internet), can you ping the gateway?

If the gateway is 192.168.1.1, try to ping that from a terminal.

If that works - can you ping an external IP address?  Google has many IP addresses, but here are two random ones you can try:

173.194.33.5
173.194.33.38

If you can ping those, then try pinging google.com directly.  If THAT fails but pinging the Google IP directly works, it's a problem getting DNS from the router.  

At worst, try setting a static IP temporarily on one of the Lubuntu machines; pick an IP in your subnet but not one DHCP could assign to another PC.  For example, if your gateway is 192.168.1.1, your netmask is 255.255.255.0, and your DHCP range is 192.168.1.100 to 192.168.1.199, pick say 192.168.1.201 as your static IP address.  Set the DNS to 192.168.1.1.  Repeat the above.  Try also changing the DNS to Google DNS or OpenDNS IPs.

---

### Post by go4usg50 on 2012-10-24
hello ahallubuntu

Tanks a lot for your help.

i will do your proposal to connect a lubuntu pc directly to a zywall lan port.

what i already did was a ping to a [www.yahoo.com](www.yahoo.com). then i took nslookup (on a linux pc with internet connection) to find the ip of [www.yahoo.com](www.yahoo.com). then i pinged this ip.
both of the pings failed. but i'm not sure if the ip is open for pings.

further i will try to connect the lubuntu pc's using a d-link soho switch, temporarly.

additional question:
are there additional options in the (l)ubuntu network settings, so that i can optimize the network settings.

kind regards

---

