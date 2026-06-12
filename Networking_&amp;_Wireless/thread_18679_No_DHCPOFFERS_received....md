---
title: "No DHCPOFFERS received..."
date: 2005-03-08
forum: Networking &amp; Wireless
---

### Post by Kalle Kabowski on 2005-03-08
Hello everyone!

My problem is as follows. I got a NetGear WG311 v2 Card. I got it recognized as wlan0 after upgrading from Warty Warthog to Hoary Hedgehog. I tried to configure it with the great networking tool but I wasn't lucky. So I tried to enter the parameters by hand into /etc/network/interfaces. It now looks like this

<------>
# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp
name Ethernet LAN card

iface wlan0 inet dhcp
wireless_essid ArcorWirelessXXXX
wireless_channel 6
wireless_enc on
wireless_keymode restricted
wireless_key XXXXXXXXXXXXXXXXXXX
auto wlan0
<---->

I got some information from my ISP (German one, called Arcor) which lists the parameters like ESSID and WEP encryption. I put these into my interfaces file as you can see above. But there is one little thing that makes me wonder. This information paper tells me that the "Network authentification" is "Shared". Is this the same as "resctricted"? I tried "shared" but it gives an error message...
OK, after Ubuntu has started, I open a terminal and do the following: Shut down eth0 in case it is up and runnning and then I try to "ifup" wlan0

<--->
$ ifdown eth0
$ ifup wlan0
<---->

This produces the following output:

<---->
root@Ax000:~ # ifup wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0f:b5:05:4a:cb
Sending on   LPF/wlan0/00:0f:b5:05:4a:cb
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
<--->

I used iwlist and it turns out, that my card got all parameters just fine... 
What should I do now? I'am trying to get this running for 3 days now...
I would really appreciate any hints!

Thanks a lot in advance!!!

Kalle

P.S.: I hope I posted all the details you need, in case there is something missing, please tell me so I can post it!
P.P.S.: There are two other PCs in the house which have the same card and run Windows XP. Everything is just fine there!

---

### Post by alastair on 2005-03-08
Not really sure. Wireless is a pain at the moment, as you might guess looking at the forums.

It might be best to try things manually for the moment.

Is the ESSID broadcasr?
Do you know your AP MAC address?

I might try :

iwconfig wlan0 ap <AP MAC>
iwconfig wlan0 key restricted <KEY>

Perhaps the ESSID as well at the start ... or a different order. I find that the manual method is more reliable sometimes.

It can be frustrating - keep looking at "iwconfig wlan0" and "ifconfig wlan0" etc.

---

### Post by tnt on 2005-03-14
I have the same problem with linksys WMP54G v4.  I upgrade my to Hoary. Wireless card seem to work great after that upgrade. However, I was only abling to have internet access for a while like 5 min then it dropped me. I have to do 
ifup wlan0 to make it runs again. It worked for a while and failed again. So then I tried ifdown wlan0 and ifup wlan0.  I recieved the same error as you did when I do ifup wlan0.  I am not quite sure what is going on =).  

I just want you to know that you are not alone in this problem  :-o  

Have you try to disable IPv6?

---

### Post by speedy2782 on 2005-03-15
When I ran into that problem I was using the wrong drivers for my card. I was using the drivers from the OEM not the chipset maker. That is one place to check

---

