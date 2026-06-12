---
title: "ubuntu8.10 hathway internet not working"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by tkcommunity on 2009-08-13
hi,
 can you help to solve the ubuntu internet problem in my system aim
sending url of problem which entered in a word doc
 [http://docs.google.com/Doc?id=dhmkhqhj_2gqf5qmcs](http://docs.google.com/Doc?id=dhmkhqhj_2gqf5qmcs)
iam having xp with ubuntu dual boot cable modem connected in lan i coudnt connect internet in ubuntu only local ip is inging default gate way dns is not pinging i have hardware checking in ubuntu it is showing follwing error
 Testing your connection to the Internet:
 ERROR:root:Could not find def gateway info in /proc
Traceback (most recent call last):
File "/usr/share/hwtest/scripts/internet_test", line 132, in <module>
sys.exit(main(sys.argv[1:]))
File "/usr/share/hwtest/scripts/internet_test", line 118, in main
host = route.get_default_gateway()
File "/usr/share/hwtest/scripts/internet_test", line 81, in get_default_gateway
t1 = self._get_default_gateway_from_bin_route()
File "/usr/share/hwtest/scripts/internet_test", line 69, in _get_default_gateway_from_bin_route
if def_gateway:
UnboundLocalError: local variable 'def_gateway' referenced before assignment
 how to solve this problem
 windows Internet settings
 Windows IP Configuration
 Host Name . . . . . . . . . . . . : latiff-cce14a68
 Primary Dns Suffix . . . . . . . :
 Node Type . . . . . . . . . . . . : Unknown
 IP Routing Enabled. . . . . . . . : No
 WINS Proxy Enabled. . . . . . . . : No
 Ethernet adapter Local Area Connection:
 Connection-specific DNS Suffix . :
 Description . . . . . . . . . . . : VIA Rhine II Fast Ethernet Adapter
 Physical Address. . . . . . . . . : 00-15-F2-C3-AB-AE
 Dhcp Enabled. . . . . . . . . . . : Yes
 Autoconfiguration Enabled . . . . : Yes
 IP Address. . . . . . . . . . . . : 60.254.96.243
 Subnet Mask . . . . . . . . . . . : 255.255.240.0
 Default Gateway . . . . . . . . . : 60.254.80.1
 DHCP Server . . . . . . . . . . . : 202.88.152.20
 DNS Servers . . . . . . . . . . . : 202.88.152.8
 202.88.152.7
 Lease Obtained. . . . . . . . . . : Monday, March 02, 2009 10:11:31 PM
 Lease Expires . . . . . . . . . . : Tuesday, March 03, 2009 10:11:31 PM
 if con fig report
 ***********************************************************************************
 i have try to open the [http://209.85.171.100]("http://209.85.171.100/") it doesn't open and have
typed sudo gedit /etc/network/interfaces in the terminal
the following report
auto loiface lo inet loopback
 network card hardware test
 ***********************************************************************************
 the procedure I have done
 Step 1 : GO to the terminal
Step 2 : Type sudo gedit /etc/network/interfaces
Step 3 : Replace whatever exists in that file with this
 auto lo
iface lo inet loopback
 iface eth0 inet static
address 60.254.96.243
netmask 255.255.240.0
gateway 60.254.80.1
 Step 4 : Save the file and close
Step 5 : then back in the terminal, type sudo gedit /etc/resolv.conf
Step 6 : add the following 2 lines to it
 nameserver 202.88.152.8
nameserver 202.88.152.7
 Step 7  : save the file and close
Step 8  : back in the terminal type sudo /etc/init.d/networking restart
 report I have got
 i have done all the things. the name servers   automatically configured by network manger
i have restarted the net work it is showing error aim sending a screen shot look the pic
 I have report this problem as a bug in the ubuntu forum
 ** Changed in: hwtest (Ubuntu)
Sourcepackagename: None => hwtest
 --
no browsing in lan connected cable broad band
[https://bugs.launchpad.net/bugs/336266](https://bugs.launchpad.net/bugs/336266)
You received this bug notification because you are a direct subscriber
of the bug.
 Status in “hwtest” source package in Ubuntu: New
 they have sent this reply I couldn't”t understand what to
 ***********************************************************************************
 broadband details
 it is a motto roala surf board cable modem it is connected by LAN net work card
 same windows configuration showing in ubuntu 8.10 in automatic dhcp but internet not working
 there is no user id password for longing just play and surf 

Thanks,
[Business Community]("http://community.tradekey.com/")

---

