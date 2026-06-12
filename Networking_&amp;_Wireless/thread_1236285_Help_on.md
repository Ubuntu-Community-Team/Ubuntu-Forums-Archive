---
title: "Help on"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by Neill_R on 2009-08-10
My Network consists of a router connected to several Windows PC and Servers. However my Internet is provided by mobile broadband a USB device plugged into this PC which is running X-UBUNTU 9.04. 

The question I have is how (in software terms) do I connect the auto eth0 interface to my routers Internet. 


Internet----->USB------->[PC]===>Eth0====>[Router]=============>[PC]

89.194.???.???                           10.x.y.A                    10..a.b.X                 10.a.b.n
Dynamic                                    static                         static                     staticDynamic 

submasks always 255.255.255.0
 

Any guidance will be much appreciated 
Thank you

---

### Post by Macchi on 2009-08-10
As I understand you need "Internet Connection Sharing", of course to share your internet connection from a mobile broadband (USB) modem to your entire local area network.

There are many cookbook recipes to achieve the same result, but the faster solution for me was:

1) Set up your mobile broadband connection through the network manager.   

2) Install Firestarter and set a connection sharing. Decide if you will have firestarter to act as DHCP server or if you have an external server.

3) Check the settings on your router and be sure to use the address of machine with the internet connection is the gateway to the internet. Don't forget to check your DNS settings on the machine (cat /etc/resolv.conf) and on the router.

With Firestarter I was able to do all the settings from a graphical interface and without messing up the IPtables.



PS: In my case the internet connection went down regularly and it had to be restarted every second day.Thus I wrote a simple script that regularly attempted to keep the internet connection alive. I have used cron and cnetworkmanager, a command-line interface for the NetworkManager.
For a professional solution that is more reliable and has lower power consumption I would recommend a [Dovado UMR router]("http://www.dovado.com/UMR.html"). It is built with Linux and costs only slightly more that a conventional router.

---

### Post by Iowan on 2009-08-10
A couple of ICS links that might help:
[https://help.ubuntu.com/community/Internet/ConnectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")
[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless")

---

