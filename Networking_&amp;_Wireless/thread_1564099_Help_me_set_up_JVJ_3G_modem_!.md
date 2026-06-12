---
title: "Help me set up JVJ 3G modem !"
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by van7hu on 2010-08-30
Hello everyone !
I have JVJ 3G modem,one from singapore.
[IMG]http://knic.vn/attachment.php?attachmentid=69&d=1278181375[/IMG]
I have try out as :[https://wiki.ubuntu.com/NetworkManager/Hardware/3G/Probing](https://wiki.ubuntu.com/NetworkManager/Hardware/3G/Probing)
But it doesn't work .
Has anyone try it before ? Please tell me how to.Thank you !

---

### Post by dineshs on 2010-08-30
Did you try configuring the connection via Network Mnager?
(Rightclick NM icon on top right of the panel-edit conn-mobile broadband-add.........)
Can you post the results of the following terminal commands?
```
lsusb
```and```
dmesg | grep -e "modem" -e "tty"
```
You can read [this guide]("http://ubuntuforums.org/showthread.php?t=1466490") by alexfish

---

### Post by van7hu on 2010-08-30
Hi [dineshs]("http://ubuntuforums.org/member.php?u=253252"),
Here is the results before I plug-in my Modem:
> 
van7hu@van7hu-laptop:~$ lsusb
Bus 008 Device 002: ID 1c4f:0003 SiGma Micro HID controller
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 5986:0145 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
van7hu@van7hu-laptop:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
And after:
> 
van7hu@van7hu-laptop:~$ lsusb
Bus 008 Device 002: ID 1c4f:0003 SiGma Micro HID controller
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1c9e:f000 
Bus 002 Device 003: ID 5986:0145 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
van7hu@van7hu-laptop:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
The only difference is : Bus 002 Device 002: ID 1c9e:f000 
As Probing page say,I use it as vendor ID and  product ID but it doesn't work.
It seems that Ubuntu (Lucid) recognize my modem as a CD drive rather than an USB.

---

### Post by dineshs on 2010-08-30
You will have to install usbmodswitch
Alefish is an expert in this field.You can send a private message

---

### Post by van7hu on 2010-09-04
Hello again,
I have installed usbmodeswitch,
I try to probe my usb as in [https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)
> 
van7hu@van7hu-laptop:~$ sudo wvdial cellular
[sudo] password for van7hu: 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+CGDCONT=1,"IP","m3-world"
AT+CGDCONT=1,"IP","m3-world"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT 7200000
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sat Sep  4 16:28:08 2010
--> Pid of pppd: 1708
--> Using interface ppp0
--> pppd: 0&#65533;/
--> pppd: 0&#65533;/
--> pppd: 0&#65533;/
--> pppd: 0&#65533;/
--> pppd: 0&#65533;/
--> pppd: 0&#65533;/
--> local  IP address 10.6.119.182
--> pppd: 0&#65533;/
--> remote IP address 10.64.64.64
--> pppd: 0&#65533;/
--> primary   DNS address 10.1.10.11
--> pppd: 0&#65533;/
--> secondary DNS address 203.162.0.11
--> pppd: 0&#65533;/
It seems to works,here is result of PING command
> 
van7hu@van7hu-laptop:~$ ping google.com
PING google.com (74.125.71.106) 56(84) bytes of data.
64 bytes from hx-in-f106.1e100.net (74.125.71.106): icmp_seq=1 ttl=47 time=107 ms
64 bytes from hx-in-f106.1e100.net (74.125.71.106): icmp_seq=2 ttl=47 time=105 ms
64 bytes from hx-in-f106.1e100.net (74.125.71.106): icmp_seq=3 ttl=47 time=103 ms
64 bytes from hx-in-f106.1e100.net (74.125.71.106): icmp_seq=4 ttl=47 time=114 ms
64 bytes from hx-in-f106.1e100.net (74.125.71.106): icmp_seq=5 ttl=47 time=101 ms
^C
--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 101.997/106.903/114.994/4.477 ms
But I still could not access any website by firefox (even google.com)
On [https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)
It says:
> 
You might have issues with resolvconf stomping on your DNS configuration in /etc/resolv.conf  - but if you're getting an IP address from the remote peer then the  modem is working, even if you can't access any websites etc. If you  don't use resolvconf, consider just uninstalling it. 
I dont understand  these lines,I try to uninstall resolveconf,but it reports that I haven't installed resolvconf before.
What should I do now ?

---

