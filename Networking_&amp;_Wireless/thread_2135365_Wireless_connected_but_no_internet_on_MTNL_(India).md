---
title: "Wireless connected but no internet on MTNL (India) connection"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by esskay303 on 2013-04-14
HI
I recently bought wireless modem D-Link DSL 2730U. Everything is working fine. The internet is connected when wired but however wireless not working. I have installed wlan and configured the connection. In fact the wi-fi is connected and i can see the connection properties also in the tray. However when i open the browser it gives me an error - not connected. I am using ubuntu 12.04. i did check additional drivers in the system settings - hardware and nothing is listed there.
Can someone please guide me what could be wrong....?
I am new to ubuntu and after going through few forum topics i did try something. in terminal i typed iwconfig and sudo modprobe -r wl and the result is as under - 

admin1@admin1-laptop:~$ iwconfig
wlan2     IEEE 802.11bgn  ESSID:"MTNL"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: F6:27:29:D8:D9:26   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.

eth2      no wireless extensions.

admin1@admin1-laptop:~$ ^C
admin1@admin1-laptop:~$ sudo modprobe -r wl
[sudo] password for admin1: 
FATAL: Module wl not found.
admin1@admin1-laptop:~$ 

Please help me....

---

### Post by TheFu on 2013-04-14
Network troubleshooting: [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

Do you have a router with an SSID configured?  My wifi settings show "managed", not "adhoc" as the connection type.

A tool like wifi-radar might help determine frequency interference for your location too.

---

### Post by esskay303 on 2013-04-14
hi....thanks...the link is not working.
yes..I have ssid configured....WIFI SETTINGS SHOW AD-HOC

---

### Post by TheFu on 2013-04-14
That link works from here ... and from Nepal - tested it last week.  Basically it has a step-by-step way to determine what issues you have having with general networking problems by starting from the machine, then the router, then internet servers, then DNS.  If DNS is used first and fails, you can't tell what is really broke. Use IP addresses all the way in your tests, until you get to the last step - THEN use DNS.

Do you have a router or is MTNL a wifi service provided by someone else?  I've never used a wifi service outside a cafe or restaurant. What sort of authentication does it require?  PPoE, radius?

Sorry, I'm no real help.

---

### Post by esskay303 on 2013-04-15
Hi Thefu....thanks..The link is finally working....
1. MTNL is one of the ISP here in India. The bandwidth is provided through telephone line. I have a wi-fi router D-Link DSL 2730U which is connected to the telephone line. From this router I get the wirefree internet in my home on all the gadgets e.g. laptops, mobile phones, tablet etc. So far there is no problem since all others are not running on Ubuntu OS.
2. In one of the laptop I am using ubuntu 12.04 and this is the one which is not connected through wireless.
3. With wire I have no problem...I get internet on ubuntu laptop also.
4. Even with wireless, the laptop is connected and I see the connection icon in the tray. However when I open browser i dont see it working.
5. MTNL authentication is PPPoE.

Can someone please guide me to fix this issue.....?

---

### Post by TheFu on 2013-04-15
I looked up that router. It is a DSL wifi-N150 router.  Having it set in adhoc mode is strange to me, since adhoc networking is almost never used. We always (99.9999%) use Infrastructure mode on our routers.  Whenever I travel anywhere, those wifi routers are in "infrastructure mode" and work fine too. Interesting.

This link [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc) discusses using adhoc networking with Ubuntu and might be just what you need to get everything working.

If you can gather the network settings for the other devices that work on your network, you might see a pattern that you could enter into the Ubuntu settings.
Did you run the commands in that link? What were the results? Did anything work?

---

### Post by chili555 on 2013-04-15
> **TheFu said:**
> I looked up that router. It is a DSL wifi-N150 router.  Having it set in adhoc mode is strange to me, since adhoc networking is almost never used. We always (99.9999%) use Infrastructure mode on our routers.  Whenever I travel anywhere, those wifi routers are in "infrastructure mode" and work fine too. Indeed. Ad-hoc is for computer-to-computer connections. Infrastructure is for computer-to-router.

---

### Post by esskay303 on 2013-04-23
Hi

I have tried every option available to me....mentioned here as well in other links but could not get it working. wireless connected sign is there but i can not connect to the internet. i have to use wired connection. i have spent ample time to get it working but unfortunately not working for me. I have given up.....

---

### Post by BharatBSahni on 2014-02-11
I got this command on the net;
 Try this for LAN always connected Internet
Type the follwoing command in the terminal 

sudo gedit /etc/network/interfaces
#Now change the text text of the file to;

#The loopback network interface

auto lo
iface lo inet loopback

#The primary network interface

auto eth0
iface eth0 inet dhcp

#Now restart & enjoy

---

### Post by TheFu on 2014-02-11
Thanks for trying to help > **BharatBSahni said:**
> 
```
#The loopback network interface
auto lo
iface lo inet loopback
#The primary network interface
auto eth0
iface eth0 inet dhcp

```
#Now restart & enjoy

However, this has ZERO to do with any wifi interface. This is for wired ethernet connections only.

Also, no need to restart the PC. Just restart the networking service if changes are made to that file.
```
sudo service networkiing restart
```

---

### Post by esskay303 on 2014-02-12
Thanks to all for your help and advise....in fact this issue was fixed a long back....i was making a little stupid silly mistake and this issue is now no more....thanks once again.....

---

