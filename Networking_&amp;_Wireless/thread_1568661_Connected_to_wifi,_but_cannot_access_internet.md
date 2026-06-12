---
title: "Connected to wifi, but cannot access internet"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by ost2life on 2010-09-05
right, so I've been using my upstairs computer with no problems recently up until this evening, when I rebooted it did an automatic scan of my disks, so I left it to it's thing and when I came back ubuntu had successfully booted, and had seemingly successfully connected to my wireless network as usual.

I've been through the wireless troubleshooting guide, paying special attention to sections 4 and 6 but to no avail, while I'm apparently connected, and have been assigned an IP by my router I'm unable to access anything outside my computer, including the router itself.

This happened before, however I solved it by reinstalling ubuntu, and I'd rather not do that again! There's a beer in it for the person who can help me fix it :)

output of ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1c:25:38:8e:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9475 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1103438 (1.1 MB)  TX bytes:1103438 (1.1 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:31:d0:28  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:1fff:fe31:d028/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1059 errors:0 dropped:0 overruns:0 frame:0
          TX packets:349 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:344345 (344.3 KB)  TX bytes:27044 (27.0 KB)

output of route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0


output of cat /etc/networking/interfaces

auto lo
iface lo inet loopback

---

### Post by ost2life on 2010-09-05
oh, and just to confirm that it's a problem with that computer, here's the readout from my router 

LAN > DHCP Client List

This page shows you the IP address, Host Name and MAC address of each computer that is connected to your network. If the computer does not have a host name specified, then the Host Name field will be blank. Pressing "Refresh" will update the list.
 
IP Address 	Host Name               MAC Address
192.168.2.3 	main-desktop	        00:19:21:E8:4D:08
192.168.2.4 	android_39ca93e7e30	00:23:76:08:00:33
192.168.2.5 	paul-desktop	        00:1F:1F:31:D0:28 <<< this is the one cause me problems

---

### Post by andymorton on 2010-09-05
I've got exactly the same problem on my computer. I'm clueless as to what's causing it. . Ironically, when I first tried to post this I couldn't do it. I had to disconnect and then reconnect. 


(a very frustrated) andy

---

### Post by ost2life on 2010-09-05
Bump

---

### Post by arvevans on 2010-09-05
In addition to WiFi and IP connectivity you need to have Domain Name Service (DNS) configured.  When you enter the textual URL for a web location, your computer sends a DNS-query to a specific DNS server.  This server returns the numeric IP address that corresponds to the URL that you entered.  Then your computer re-initiates it's connection request using this IP address that it got from the DNS server.

Before trying to set up DNS, we need to determine if this is really your problem.  You can do this by accessing something out on the Internet using it's numeric IP address instead of entering it's textual URL in your browser.  For instance, the numeric IP address for google is 74.125.155.99  so you can go to your browser and enter "http://74.125.155.99/".  This should get you to a Google page.  If this works then your problem may be lack of a DNS server or local DNS services.  If it does not work, then you have some other problem that may not be DNS related.

There are several excellent tutorials available on-line to help you configure your DNS functions and to assign a DNS server.  One readily available open DNS server would be that provided by Google.  Their DNS server IP addresses are at 8.8.8.8 and 8.8.4.4
I have found their DNS service to be fast and reliable.

You can also go to a terminal page and enter "ping -c3 8.8.8.8" to see if your computer is actually passing commands to the Internet and receiving them back from Internet based entities.

---

### Post by ost2life on 2010-09-06
Thanks for the reply, as I said though, I've been through thr wireless networking troubleshooter including the checking of my dns settings. Just to make my problem clear though, the computer boots without error, connects to my network fine and according to syslog is able to connect to and negotiate with my router and receive its IP. The router shows it on the DHCP client list and network manager shows the relevant and correct details. However I cannot connect to any external server using either normal [www.server.com](www.server.com) dns addresses or IP. I can ping localhost but not the ip address of my router 192.168.2.1, nor any other server.

That's about as thorough as I can be right now.

---

### Post by ost2life on 2010-09-06
Bump

---

