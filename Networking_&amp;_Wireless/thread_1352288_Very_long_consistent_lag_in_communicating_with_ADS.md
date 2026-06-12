---
title: "Very long consistent lag in communicating with ADSL router/modem Karmic"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by spin on 2009-12-11
Hi,

it seems that computers using Ubuntu Karmic and my router/ADSL modem don't get along very well. I first assumed it was because of a lag in the communication between the modem and the server, but then I connected a Mac (MacBook Pro, OSX 10.5) to the same wireless network, and it works like a charm.

The problem is that there is an extreme lag in connecting to anything through my router using any of my two Ubuntu laptops (Dell Vostro 1400 and Lenovo S10e), both wirelessly and through a cable. For instance, when trying to access a web page, the browser takes a very long time just "searching for [web address]" (i.e. the progress meter in Firefox is empty) before it actually starts loading the web page. But this is not only a problem for web browsing. All programs connecting to the internet have problems, both with timeouts and a slow connection once actually connected. Pinging a server is very much slower on my Ubuntu computers than using the Mac.

Does anyone know what the cause of the problem might be? I'd be very grateful for any and all help.

Below are the outputs from ifconfig (for the wireless card) on the Mac and one of my Ubuntus. If any other kind of output is required, please let me know:

Mac ifconfig:
> 
en1: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	inet6 fe80::21e:c2ff:fec4:83d4%en1 prefixlen 64 scopeid 0x5 
	inet 192.168.1.50 netmask 0xffffff00 broadcast 192.168.1.255
	ether 00:1e:c2:c4:83:d4 
	media: autoselect status: active
	supported media: autoselect


Ubuntu ifconfig:
> 
wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:73:57:fa 
          inet addr:192.168.1.52  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe73:57fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2557 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2790213 (2.7 MB)  TX bytes:432204 (432.2 KB)


---

### Post by gordintoronto on 2009-12-11
Are the Ubuntu computers using different DNS servers than the Mac?  To display the DNS servers in Ubuntu:

cat /etc/resolv.conf

---

### Post by wewantutopia on 2009-12-11
I've been experiencing the same problem.  Also using Karmic.  Once Network Server finally opens and displays the name of my home network, it always fails to mount the samba shares.  I've been using the same smb.conf for a year without any problems until Karmic upgrade.


Edit:  actually the internet is working fine, it's just the network... maybe it's not the same problem.

---

### Post by spin on 2009-12-11
gordintoronto: The outputs from both computers look like this:

Mac:
> domain localdomain
nameserver 192.168.1.1


Ubuntu:
> nameserver 192.168.1.1


That is, the Ubuntu computer is lacking the first line from the Mac, "domain localdomain". Can you tell me what this means, if anything?

---

### Post by spin on 2009-12-11
Hey again,

it seems that my /etc/resolv.conf on my Ubuntu computer is changing over time. Now, the output of cat /etc/resolv.conf is the following (still connected to the same network):

domain localdomain
search localdomain
nameserver 192.168.1.1

---

### Post by gordintoronto on 2009-12-11
If you have a DHCP connection, Network Manager creates resolv.conf with each connection.

If you have a static IP, resolv.conf can be edited manually, and it stays the way you make it.

---

### Post by spin on 2009-12-11
Yes, I am using DHCP to connect to the router. Do you suggest I use a static IP to resolve the lag problem?

---

