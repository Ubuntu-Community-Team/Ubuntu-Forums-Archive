---
title: "wired internet stops working. no ping."
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by kokadu on 2011-01-09
hello forum!
background to the situation now:i wanted to log on to our wireless internet. this didnt work out. i decided to stick to the wired one. i deinstalled some of the programs needed for the wireless connection. but now even the wired one doesnt work any more.


  my network manager and even the nm-applet is desinstalled now. reinstallation didnt work (by going to ubuntu download site, and transferring the downloaded packages to an usb stick and taking it over to my laptop without internet). i reinstalled the dhcpd package. this seemed to work.
 

 please find below the terminal answers.
 the wired internet is for sure working (tested on other computers). it is also not the hardware, because i have dual boot and it is working on the windows side.
 

 i have been surfing all the forums . and didnt find the answer so far. any ideas? thanks a lot for any advice!

 

 ifconfig:
 
[PHP]
                                 lo        Link encap:Lokale Schleife   
           inet Adresse:127.0.0.1  Maske:255.0.0.0  
           inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine  
           UP LOOPBACK RUNNING  MTU:16436  Metrik:1  
           RX packets:3994 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:3994 errors:0 dropped:0 overruns:0 carrier:0  
           Kollisionen:0 Sendewarteschlangenlänge:0  
           RX bytes:254100 (254.1 KB)  TX bytes:254100 (254.1 KB)  
 

 [/PHP]
                                 ping: bbc.co.uk (212.58.22.85)   both didnt work
 

                                 sudo vi /etc/network interface
[PHP]
 # This file describes the network interfaces available on your system  
 # and how to activate them. For more information, see interfaces(5).  
 

 # The loopback network interface  
 auto lo  
 iface lo inet loopback  
 

 # The primary network interface  
 auto eth0  
 #iface eth0 inet dhcp  
 ~                                                                                
 ~                                                                                
 ~                                                                                
 ~                                                                                
 ~                                                                                
 ~                                                                                
 ~                                                                                
 ~                                                                                
 ~                                                                                
 ~                                                                                
 ~                                                                                
 ~                                                                                
 ~                                                                                
 Type  :quit<Enter>  to exit Vim 

[/PHP]

---

### Post by drdos2006 on 2011-01-09
This is from a previous thread I saved because it helped me.
> 
You may be having connection issues because of IPv6 even though it shows an IPv4 connection. 

 How do I prove ipv6 has been successfully disabled
There seems to be much disagreement between distros regarding how ipv6 is disabled, even between different versions of the same distro. Rather than just follow instructions for disabling ipv6 for a given distro, I would like to also test that ipv6 is not used any more. Any software or executable that relies on ipv6, that I can use to confirm that ipv6 has been successfully disabled?

cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf

Code:

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
ifconfig should not mention an IPV6 address on any interface after you have rebooted.

IPV6 should still be considered in your security setup on your machine, just in case it is, for example, re-enabled after an upgrade etc.

To check if IPv6 is enabled, just simply use netstat:

Code:

netstat -tlv

If you see any "tcp6" entries, then IPv6 is not disabled.

You may be also having IPv6 problems in your browser.
For Firefox, type about:config in the browser bar.
Filter with network.dns
Change IPv6disabled to true
Restart Firefox.


regards

---

