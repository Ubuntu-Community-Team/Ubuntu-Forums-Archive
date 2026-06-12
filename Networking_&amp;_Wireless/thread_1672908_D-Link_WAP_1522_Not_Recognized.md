---
title: "D-Link WAP 1522 Not Recognized"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by HouTex on 2011-01-21
I'm brand new to Ubuntu having just received my new Dell with 9.1 this week. So far, I like it. Right out of the box it located one of my wireless access points (an old Linksys) and connected to it with no problems. However, I have another WAP in our master bedroom (a D-Link WAP 1522) because the signal from the Linksys is weak in that room. The D-Link works fine with my Blue Ray DVD player and an HP laptop (running Windows Vista Business), but my new Ubuntu does not see the D-Link--even when it's inches away. It will still try to connect to the Linksys (and it does although the signal can be very week) and it also sees a neighbor's WAP. Any ideas?

---

### Post by HouTex on 2011-01-22
UPDATE:

I finally connected to the WAP, but it was odd that the WAP never showed up as being available.  I created a new network and typed in the name of the WAP and it asked for the password key and then I was in.

But the problem now is that Firefox won't connect to the internet through the D-Link WAP.  But it still works fine with the Linksys WAP.  Are there any obvious settings that will fix this?

---

### Post by HouTex on 2011-01-23
I'm still not able to use Firefox to connect to the internet through the D-Link.  While connected to the D-Link here is the output when I typed ifcong:

david@dell-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:b9:68:d4:a0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 1c:65:9d:98:4c:a0  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::1e65:9dff:fe98:4ca0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8743 errors:0 dropped:0 overruns:0 frame:81079
          TX packets:7339 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6213013 (6.2 MB)  TX bytes:1644658 (1.6 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:896 (896.0 B)  TX bytes:896 (896.0 B)

In other similar threads people suggested to make sure WEP encryption is used versus WPA (but then my Blue Ray DVD didn't work).  Someone also said to make sure that "no proxy" is selected.  I tried those fixes but Firefox still will not connect.  Any ideas?  Thanks in advance.

---

### Post by chili555 on 2011-01-23
> eth1 Link encap:Ethernet HWaddr 1c:65:9d:98:4c:a0
inet addr:[COLOR="Red"]10.42.43.1[/COLOR] This looks like an ad-hoc connection, not infrastructure. What are the equivalent settings when using the Linksys?

Is the D-Link repeating the signal from the Linksys? Or...??

---

### Post by HouTex on 2011-01-24
Here are the settings from the Linksys:

david@dell-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:b9:68:d4:a0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 1c:65:9d:98:4c:a0  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1e65:9dff:fe98:4ca0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:168017 errors:0 dropped:0 overruns:0 frame:33928
          TX packets:89894 errors:5 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:246575239 (246.5 MB)  TX bytes:7375225 (7.3 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)


The Linksys WAP connection is set up as infrastructure.  I'll make sure that the D-Link connection is also.  The D-link should not be repeating--if I understand what that means.  The D-Link is connected to my router through the ethernet.  The Linksys is first connected to a switch and the switch is connected to the router through the ethernet.  Each WAP has separate login/password keys.  Sorry, about some of the terms.  I'm a linux noob.  Thanks for your helpl

---

### Post by HouTex on 2011-01-24
I changed the setting on the D-Link connection to infrastructure, but it still does not connect to the internet with Firefox.  But I can access my Windows network so I'm clearly making a connection.

---

### Post by chili555 on 2011-01-24
> eth1 Link encap:Ethernet HWaddr 1c:65:9d:98:4c:a0
inet addr:[COLOR="Red"]192.168.0.101[/COLOR] Notice, the Linksys gave you a 192.x address, the usual for a computer to router connection. Please make sure the D-link is set to infrastucture mode and that your wireless card is in Managed mode:> $ iwconfig eth1
eth1      IEEE 802.11abg  ESSID:"mylilrouter"  
          Mode:[COLOR="Red"]Managed[/COLOR]  Frequency:2.462 GHz  Access Point: 99:24:56:88:D7:99   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm If it's not, switch it:```
sudo iwconfig eth1 mode managed
```Then I think you'll be all set.

---

### Post by HouTex on 2011-01-24
I will try it out tonight.  I appreciate your help.

---

### Post by HouTex on 2011-01-24
I did that and it still does not work.  Thanks for your help though.

---

### Post by HouTex on 2011-01-25
Out of curiosity, I tried to connect an old HP laptop running Windows Vista Business. It had trouble connecting to the D-Link 1522 as well. The default settings that worked with the Linksys WAP (using WEP encryption) would not work. Once I configured my connection in Vista to WPA/TKIP and input the correct key it connected to the D-Link.
 
Does this help diagnose the problem? Again, I can connect to the D-Link with ubuntu 9.1 but not to the internet. Thanks in advance.
 
And one more thing, I logged on to the D-Link WAP and disabled encryption and it still would not work.

---

### Post by HouTex on 2011-01-31
I have quit trying to connect to the D-Link 1522.  It's a good thing that the 1522 comes with female RJ-45 connections--the wired feature works just fine.
 
But now the problem is that while connected to the Linksys WAP when my computer goes to sleep I somehow lose the Linkysis wireless connection and then the computer somehow finds the D-Link 1522 WAP and automatically appears to connect to it (even though it never shows up as an available network in the Network Manager).  I say that it appears to connect to it because it will say that it's connected to the 1522 even when the WAP is unplugged.  How is that possible?  To fix it, I have to first disconnect from the 1522 through the Network Manager, and then reboot the computer which will then automatically connect to the Linksys WAP on restart.  If I just disconnect from the 1522 and reconnect to the Linksys it will not allow me to access any network resources (no internet, no network printer, no shared files, etc.).  This is a PITA.  I've tried going into system/preferences/network connections and deleting the name of the 1522 (it's odd that the 1522 shows up there, but not in the Network Manager that you access in the upper right portion of the toolbar), but it still somehow finds the 1522 and says that it's connected to it.  Any ideas?  Thanks in advance.

---

### Post by HouTex on 2011-02-23
I finally figured this out.  The D-Link is duel mode (2.4 GHz/5 GHz) and mine was set to 5 GHz to better serve the Blue Ray DVD player (that was the reason for another WAP in my home).  My Dell 1397 card (Broadcom 4312) does not support 802.11n/5 GHz speed so neither Wicd nor Network Manager would "see" the D-Link 1522 (although my old HP laptop running Windows Vista had no problem connecting to it).  I changed the settings to 2.4 GHz running on channel 11 (my other WAP is running on channel 6) and both show up in Wicd and right now I'm connected to the D-Link.  And I just tested the DVD player and I don't notice a difference in the 5 GHz vs. the 2.4 GHz--at least not yet.

It was a hardware issue all along.  If the DVD player does not work well at 2.4 GHz I might upgrade my wireless card to one that is compatible with 802.11n and 5GHz.

---

