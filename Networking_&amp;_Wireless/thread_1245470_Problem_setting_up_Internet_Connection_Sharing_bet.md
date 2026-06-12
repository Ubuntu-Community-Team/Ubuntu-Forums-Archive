---
title: "Problem setting up Internet Connection Sharing between 2 linux systems"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by HsystemX on 2009-08-20
Hi,

For some reason im unable to set up succesfully internet connection sharing between 2 linux computers. 

The PC connected to the internet (wireless) is Ubuntu 8.10, the network interface that connects to the internet is wlan0.

I have 2 more interfaces inactive, that is eth0 and eth1 (2 lan ports). I have done the steps: 

[https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing)

And also tried this one:
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

Really no luck. 

Had assigned to the client PC, which is a Linux Mint 7, ubuntu 9.04 based, setting static, or dynamic, no luck.  

Static to: 192.168.0.100 , also tried .0.2 and .0.10
With netmask: 255.255.255.0
Gateway: 192.168.0.1 (because the interface eth0 in server up with that ip)
DNS: 192.168.0.1  , also tried opendns

---

### Post by Iowan on 2009-08-20
The internet(8.10) machine ia accessing the internet OK? Can the client machine **ping** the internet machine? **ifconfig -a** on the client machine confirms an IP address(.100, .02, or .10?

---

### Post by HsystemX on 2009-08-24
>>Yes, the gateway pc is able to access the internet.

>>Im not able to ping gateway from client.

>>(client) It doesnt matter if i setup dnsmasq or ipmasq in server/gateway, it will not get automatically an ip from the gateway

>>However if i follow the process that involves using opendns for example, it doesnt work.

>>Im assigning ip manually to client (following instructions from the official manual).

>>I believe that the problem isnt the lan cable, because i can do ICS from Windows to Linux (same client laptop) without problem. 

Thanks in advance.

---

### Post by superprash2003 on 2009-08-24
post output of **ifconfig** from the terminal . does the client get an ip address?

---

