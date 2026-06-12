---
title: "Wireless and eth0 connections run real slow"
date: 2010-09-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by egrpioneer on 2010-09-20
The issue seems to be isolated in 10.10. Had no problems with 10.04 LTS. 10.10 daily updates download @ ~ 10 Kb/sec. 
My PC has a multiple HDD config. and dual boots XP (for my wife) and 64 bit 1010 beta. XP seems OK.
The laptop just runs 64 bit 1010 beta.

Ubuntu forum and other internet searches seem to point to issues with network manager. 
Thanks in advance for any suggestions/solutions.

---

### Post by cariboo on 2010-09-20
Doing updates over the last week, neywork speeds have been up and down, at times it's been 20-30kb, and other time it's been 1200+kb. See as you have two systems with Ubuntu on them, you can do some testing between computers to check the network speed, of course your network speed is only going to be as fast as the slowest device.

Install iperf on each system, it's in the repositories. Iperf is a command line app. so open a terminal on both systems. Make one the server by typing the following command:

```
iperf -s
```

on the other system type:

```
iperf -c <computer name>
```

where <computer-name> = the name of the computer the iperf server is running on, or it's ip address.

This is the result i get using a wired connection:

```
iperf -c willy
------------------------------------------------------------
Client connecting to willy, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.215 port 41280 connected with 192.168.1.250 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    113 MBytes  94.6 Mbits/sec
```

and this is the result for a wireless connection:

```
iperf -c chilanko
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.104 port 50502 connected with 192.168.1.215 port 5001
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  27.5 MBytes  23.0 Mbits/sec
```

I have a 100Mbps network, so the results are as expected. If you get the correct network speed internally, but slow speeds on the internet, check for other problems.

---

### Post by egrpioneer on 2010-09-20
> **cariboo907 said:**
> Doing updates over the last week, neywork speeds have been up and down, at times it's been 20-30kb, and other time it's been 1200+kb. See as you have two systems with Ubuntu on them, you can do some testing between computers to check the network speed, of course your network speed is only going to be as fast as the slowest device.

Install iperf on each system, it's in the repositories. Iperf is a command line app. so open a terminal on both systems. Make one the server by typing the following command:

```
iperf -s
```

on the other system type:

```
iperf -c <computer name>
```

where <computer-name> = the name of the computer the iperf server is running on, or it's ip address.

This is the result i get using a wired connection:

```
iperf -c willy
------------------------------------------------------------
Client connecting to willy, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.215 port 41280 connected with 192.168.1.250 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    113 MBytes  94.6 Mbits/sec
```

and this is the result for a wireless connection:

```
iperf -c chilanko
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.104 port 50502 connected with 192.168.1.215 port 5001
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  27.5 MBytes  23.0 Mbits/sec
```

I have a 100Mbps network, so the results are as expected. If you get the correct network speed internally, but slow speeds on the internet, check for other problems. 

Thank you for your response and trouble shooting process. I'll run it tonight and report back.

My ISP can only offer me DSL because I'm at the central office outer limit (25000 ft.) I can only get up to 1.4 MB's/sec. without packet loss and dropped connections.

---

### Post by cariboo on 2010-09-20
With a connection that slow, the best transfer speed you're going to see is about 179.2 KB/S from the internet

---

### Post by egrpioneer on 2010-09-20
> **cariboo907 said:**
> With a connection that slow, the best transfer speed you're going to see is about 179.2 KB/S from the internet

Yeah, that's about max. on a good day! Comcast is an option, but their service does not exist. Waiting for Uverse to make it into our neighborhood.

---

### Post by egrpioneer on 2010-09-20
> **cariboo907 said:**
> Doing updates over the last week, neywork speeds have been up and down, at times it's been 20-30kb, and other time it's been 1200+kb. See as you have two systems with Ubuntu on them, you can do some testing between computers to check the network speed, of course your network speed is only going to be as fast as the slowest device.

Install iperf on each system, it's in the repositories. Iperf is a command line app. so open a terminal on both systems. Make one the server by typing the following command:

```
iperf -s
```

on the other system type:

```
iperf -c <computer name>
```

where <computer-name> = the name of the computer the iperf server is running on, or it's ip address.

This is the result i get using a wired connection:

```
iperf -c willy


------------------------------------------------------------
Client connecting to willy, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.215 port 41280 connected with 192.168.1.250 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    113 MBytes  94.6 Mbits/sec
```

and this is the result for a wireless connection:

```
iperf -c chilanko
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.104 port 50502 connected with 192.168.1.215 port 5001
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  27.5 MBytes  23.0 Mbits/sec
```

I have a 100Mbps network, so the results are as expected. If you get the correct network speed internally, but slow speeds on the internet, check for other problems.

Here is the iperf output.
Thank you in advance for your analysis.

------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.140 port 5001 connected with 192.168.1.104 port 54574
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.3 sec  25.8 MBytes  21.0 Mbits/sec



------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.104 port 54574 connected with 192.168.1.140 port 5001
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.1 sec  25.8 MBytes  21.4 Mbits/sec

---

### Post by cariboo on 2010-09-20
That looks OK for a wireless connection, so it looks like the drivers are working properly. It may be a dns problem that is causing a slow internet connection. How do you connect to the internet?

---

### Post by egrpioneer on 2010-09-20
Is there a terminal command that I can use to help answer the question?

---

### Post by egrpioneer on 2010-09-21
Network Manager in default mode is used. Regarding DNS issues, that does seem to be a cause of the problem. I've read bug reports that go back over the past several months. Is a permanent solution being considered?

---

### Post by cariboo on 2010-09-21
I always set manual ip addresses using network manager, so I don't have a problem with DNS, I did have a slow connection just after an install about a month ago, but setting the dns servers manually seemed to cure the problem.

---

### Post by egrpioneer on 2010-09-21
OK, I'll try it. Will the address and netmask that I use be unique to my network?

---

### Post by cariboo on 2010-09-21
It depends on how your ip address are assigned. If your router/modem assigns ip addresses, they have to be in the same net block, for example, if your DHCP assigned ip address is 192.168.1.5, than anything in the range of 192.168.1.2 to 192.168.1.254 will be OK. I usually set my static ip addresses above the range that DHCP does, I have my router set to only assign 5 DHCP addresses, between 192.168.1.100 and 192.168.1.105, so anything below 192.168.1.99, and above 192.168.1.106 will work.

The netmask will almost always be 255.255.255.0, and the gateway address would be your router/modem's internal ip address.

---

### Post by iClouseau88 on 2010-09-21
Hello cariboo907,

I looked at your attached thumbnail sketch.  Regarding  your "IP = 64.59.168.13", is this the same as WAN IP rather than your router's internal IP (i.e., 192.168.1.1)?  

My Netgear N router, with DD-WRT firmware, shows "IP Address =6x.5x.168.1x" for WAN.

---

### Post by cariboo on 2010-09-21
> **iClouseau88 said:**
> Hello cariboo907,

I looked at your attached thumbnail sketch.  Regarding  your "IP = 64.59.168.13", is this the same as WAN IP rather than your router's internal IP (i.e., 192.168.1.1)?  

My Netgear N router, with DD-WRT firmware, shows "IP Address =6x.5x.168.1x" for WAN.

No 64.59.168.13 is my isp's DNS address. The one thing you won't see here is my public ip address. :) I set everything to manual including the DNS address. It looks like you're with Shaw Cable too.

I use a Cisco/Linksys WRT310N. This is what my router status page looks like.

---

### Post by iClouseau88 on 2010-09-21
Hello cariboo907,

Sorry I didn't mean to be nosy about your public IP address, if it appears that way.  I was asking to confirm so that I can take another look at my router's DD-WRT page before fiddling around with DNS settings. You can see over Networking & Wireless sub-forum that I am having a problem with slow bit rate in Linux but not in Windows 7.  By the way, how do I show thread number so that I don't have to make reference to the thread title?  I should have thought of setting up static address for wireless networking. At present it is via DHCP.

My ISP is probably a sub-contractor or reseller of Teksavvy which buys bandwidth from Bell Canada.

---

### Post by cariboo on 2010-09-21
The DD-WRT status page is quite similar to the Linksys page, the DNS address should be listed, I've also got a Google DNS server address that I added manually, it really doesn't seem to make any difference.

On the IPV4 page, when you enter your internal ip address, netmask and gateway, you have to press enter after adding each address. If you enter more than one DNS server address, seperate them with commas. IF things don't seem to work any better, you can always go back to automatic settings.

---

### Post by iClouseau88 on 2010-09-21
Hi,

Problem solved after I edited wireless connection for MANUAL setup. I only see the bit rate increased from 2 Mbps to 14 Mbps, but this is better than nothing.  Thanks for your suggestion about using static DNS instead of DHCP.

---

