---
title: "Wifi Help!!!!!!!!!!!"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by mini260462 on 2011-01-08
:confused:Hi All! Newb here so be gentle! I have an ASUS 4g netbook with ubuntu netbook installed. I have tried in vain to get onto my home network and even though it states connected I cannot load any web pages!! I have just bought the said netbook to work to try a 'free' wifi zone and entered the password and Hey Presto! I'm on the net. I have seen many posts about wifi problems but I cannot find a soloution. 

I am thinking the problem is with the encryption as I can get on this free wifi no problem. I only bought this netbook for my daughter to surf the net, so it is gonna be useless at home if I can't connect.

I know one of you genie's out there can help me!!

I am very familiar with windows but new to Linux so please be gentle with me!

Thanks in advance

Bec

---

### Post by ugm6hr on 2011-01-08
If it works on a free wifi network, the problem is clearly not with the driver.
What wifi router do you use at home?
What encryption does it use?
I know that there have been porblems with the Orange UK routes, which default to combined WEP/WPA, which Ubuntu can't cope with.
It would be helpful to see what wifi card you have anyway...
When trying to connect to the home network, enter the following and post the response back here:
```
lshw -class network
```

---

### Post by mini260462 on 2011-01-08
Thank you I will try this when I get home, the mobile broadband I use is Orange although the signal is pretty weak. At home I have a 50mb broadband connection with a d-link wifi router which is wpa & wpa2 with TKIP. I enter the password and it says connected but the signal indicator at the top is not lit and I cannot connect to any webpages!! V. frustrating!!

Bec:(

---

### Post by Bucky Ball on 2011-01-08
Hi again, Bec.

Are you using static IP address or getting one from the router? Do you know how to get into the configuration of your home router? Do the details on your router (ESSID = network name, security key) match what you have when you right click the Network icon->Edit Connections->Wireless???

---

### Post by mini260462 on 2011-01-08
The only problem I have is that when my router set up the network the name it gave is BEXA but the A has an accent on it, but I don't know how to enter this A with the accent in Ubuntu? Would this make a difference?

Thanks

---

### Post by Bucky Ball on 2011-01-08
Easiest? Get into the router and change the network name and security key. That way you know for sure what they both are. Then, make sure these details match on your local machine.

Post back if you can't work out how to do that. ;)

---

### Post by ugm6hr on 2011-01-08
> **mini260462 said:**
> Thank you I will try this when I get home, the mobile broadband I use is Orange although the signal is pretty weak. At home I have a 50mb broadband connection with a d-link wifi router which is wpa & wpa2 with TKIP. I enter the password and it says connected but the signal indicator at the top is not lit and I cannot connect to any webpages!! V. frustrating!!

Bec:(

Orange Mobile broadband (i.e. 3G) dongle works perfectly with Ubuntu - but that's a different issue.
D-Link router with WPA/TKIP should work fine.
I'm unsure whether the accent matters - do you have the SSID hidden (i.e. have to enter it manually)?
Have you tried going closer to the router to see if the signal strength improves?
Are there any other local wifi networks? Sometimes, if there are 2 using the same wifi channel, they can interfere with each other. If so - try changing your router to a different channel.

---

### Post by mini260462 on 2011-01-08
Not sure how to change router to another channel? 
It seems weird because I have 2 laptops and a macbook on the network already but it will not recognise this netbook! I have just tried to connect to another network I set up before and in the available drop down the chosen network is **blacked out** - with a little tv symbol to the right, next to the secure network symbol. You cannot then click on that particular network to make any changes?

I really don't want to set a 3 laptops up again as well as this netbook, but I will if I have to!!

OK so I have tried connecting to 3 different networks now and no success, I'm not sure where to go from here. The network I used at work was free but I still had to enter a password to get access and that worked fine not sure what encryption is used. I still think it must be something to do with the encryption or WPA settings at home as it thinks it's connected?

I have searched other peoples problems and I am not the only one having these issues, my router has a button to press to connect is there anything in Ubuntu (like in windows) that I can set up the wifi in this way???

It's driving me crazy now!!!

---

### Post by mini260462 on 2011-01-09
Right, I can connect with ethernet cable and with my orange usb dongle, but cannot connect through the D-link 615 with the wifi!

I have run the code (while using my orange usb) as mentioned in an earlier thread and this is what came back - 

teagan@teagan-701:~$ lshw -class network
WARNING: you should run this program as super-user.
 *-network
      description: Ethernet interface
      product: L2 Fast Ethernet
      vendor: Atheros Communications
      physical id: 0
      bus info: pci@0000:03:00.0
      logical name: eth0
      version: a0
      serial: 00:22:15:10:42:ea
      width: 64 bits
      clock: 33MHz
      capabilities: bus_master cap_list rom ethernet physical
      configuration: broadcast=yes driver=atl2 driverversion=2.2.3
firmware=L2 latency=0 multicast=yes
      resources: irq:43 memory:fbfc0000-fbffffff memory:fbfa0000-fbfbffff
 *-network
      description: Wireless interface
      product: AR5001 Wireless Network Adapter
      vendor: Atheros Communications Inc.
      physical id: 0
      bus info: pci@0000:01:00.0
      logical name: wlan0
      version: 01
      serial: 00:15:af:b3:cd:be
      width: 64 bits
      clock: 33MHz
      capabilities: bus_master cap_list ethernet physical wireless
      configuration: broadcast=yes driver=ath5k
driverversion=2.6.35-24-generic firmware=N/A latency=0 multicast=yes
wireless=IEEE 802.11bg
      resources: irq:18 memory:fbef0000-fbefffff
teagan@teagan-701:~$

It has to be something to do with the way the router is set up! But like I mentioned before the mac and 2 windows 7 laptops work fine and the desk top is ethered to it, plus we also have the ipod touches connected and a blackberry!! So I know the router works.


I have just entered the details for my home network again, and it says connection established BUT the wifi log at the top is not lit and hovering over it shows the network but it is blacked out it has the little tv and a locked wifi logo to the right and they are also blacked out. In the wireless networks section above their is the option to disconnect???

---

### Post by ugm6hr on 2011-01-09
It appears that your wifi card has had problems for some...
[http://www.linuxjournal.com/content/ubuntu-1010-maverick-meerkat-one-hit-one-miss](http://www.linuxjournal.com/content/ubuntu-1010-maverick-meerkat-one-hit-one-miss)
There are 2 comments on that page that suggest this may be a problem with the netbook edition (i.e. works with desktop), but I don't understand how that might be possible.

Others who you might like to look / converse with:
[http://newyork.ubuntuforums.org/showthread.php?t=1655738](http://newyork.ubuntuforums.org/showthread.php?t=1655738)
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/647650](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/647650)

---

### Post by mini260462 on 2011-01-11
Thanks for the links but like I said, I took the netbook to work on Saturday and connected to the free wifi there fine, that does need a password but not sure how it's set up till I can speak to someone else.
I can also get on the net fine with my Orange USB. 

I cannot connect through my home network which is virgin 50mb, with a virgin modem and a D-Link 615 wifi router. My current home network is WPA Personal, encrypted by TKIP. The netbook says connection established but the icons are all blacked out and the webpage says server unreachable. I'm not sure how to manually set the router to a different form of security?

I don't want to mess up as there are at least 5 wifi items on this network and my kids need the net for school work!

---

### Post by PatchesTheCaveman on 2011-01-11
Connect to your wireless and try running:
```
sudo dhclient wlan0
```

That will force your computer to try and get an IP address from your router.  If it still doesn't work, copy and paste the output from that along with the output from these commands:
```
sudo iwconfig
ifconfig -a
ip route
```

---

### Post by mini260462 on 2011-01-11
OK, so I checked with the guy at work and they are using WPA- personal and TKIP too (and it works there).

So here are the results from the first set of instructions - 

teagan@teagan-701:~$ sudo dhclient wlan0
[sudo] password for teagan:
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:15:af:b3:cd:be
Sending on   LPF/wlan0/00:15:af:b3:cd:be
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
teagan@teagan-701:~$

Strange about the leases and sleeping??? But what does it mean?

---

### Post by mini260462 on 2011-01-11
And here are the results from the second set of commands - Hope you can help patches!!

teagan@teagan-701:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"BEX\xC3\x82 VIRGIN"
         Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 9A:05:E5:8D:88:0C
         Tx-Power=20 dBm
         Retry  long limit:7   RTS thr:off   Fragment thr:off
         Encryption
key:B819-7030-746D-9828-E232-B219-6718-C778-D78B-1A2D-D4AA-E117-D78B-1A2D-D4AA-E117
         Power Management:off

teagan@teagan-701:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:22:15:10:42:ea
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
         Memory:fbfc0000-fc000000

lo        Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:84 errors:0 dropped:0 overruns:0 frame:0
         TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:6448 (6.4 KB)  TX bytes:6448 (6.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:b3:cd:be
         inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
         inet6 addr: fe80::215:afff:feb3:cdbe/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:24045 (24.0 KB)

teagan@teagan-701:~$ ip route
10.42.43.0/24 dev wlan0  proto kernel  scope link  src 10.42.43.1  metric 2
169.254.0.0/16 dev wlan0  scope link  metric 1000
teagan@teagan-701:~$

---

### Post by PatchesTheCaveman on 2011-01-12
Have you tried resetting your router?  I assume all the other devices on the network work fine?

It's very odd that other networks work on your computer and your computer works on other networks.

---

### Post by ugm6hr on 2011-01-13
> **mini260462 said:**
> ```
ESSID:"BEX\xC3\x82 VIRGIN"
```

Does this look correct?
I think it must be the way your router is named that is causing the problem.

---

