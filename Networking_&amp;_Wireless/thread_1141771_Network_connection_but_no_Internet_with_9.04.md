---
title: "Network connection but no Internet with 9.04"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by doriard on 2009-04-28
I installed Ubuntu 9.04 on my laptop and with this version of Ubuntu and least the wireless adapter now works -- I can connect to my home network.  However, I can't get a connection to the Internet.  I tried both DHCP and manual IP and gateway, but it made no difference.  When I dual boot to Vista I have no problem getting an internet connection through DHCP.  What else needs to be done to get a connection to the Internet in Ubuntu 9.04?

---

### Post by doriard on 2009-04-28
I discovered that my subnet mask on the Linksys router is 255.255.252.0 instead of 255.255.255.0.  This may be why it's not working.  How can I change the subnet mask back to what it should be?

---

### Post by Iowan on 2009-04-28
I don't have a Linksys router, so I can't give you the default address (192.168.1.1 from web search), but you should be able to access the configuration page from a web browser. Worst case, there should be a "reset" button to return to factory defaults.

---

### Post by doriard on 2009-04-28
I called Linksys tech support and they said the subnet mask is not set by the router.  I also verified that the subnet mask is 252.0 under Windows Vista and internet connectivity is fine there.  Vista has a subnet mask of 255.0 but the router is using 252.0, possibly from the cable modem.  It works in Vista but not Ubuntu.  I tried resetting the modem and router and it made no difference.  Now I'm back to square one.

---

### Post by doriard on 2009-04-28
It finally started working, but mostly by accident.  I accidentally created a second instance of my home network.  When I saw there were two I deleted one -- it happened to be the one that was connected to my home network.  When I deleted it, it disconnected from the network.  Then a window popped up asking me if I wanted to "allow the keyring to access the password..." or something like that, for the other instance of my network.  I said yes and everything started working.  Apparently everything was configured correctly in the first place using DHCP, but Ubuntu needed a kick-start to initialize it.

---

### Post by ajhenry777 on 2009-04-28
I am having the same problem with a Netgear router. Here is some terminal info. I'm hoping that it will be useful in diagnosing and solving the problem...

  	 	 	 	 	 	  ifconfig
 

 eth0      Link encap:Ethernet  HWaddr 00:22:15:7e:cc:91   
           inet addr:192.168.15.121  Bcast:192.168.15.255  Mask:255.255.255.0 
           inet6 addr: fe80::222:15ff:fe7e:cc91/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:1237 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:1026 errors:0 dropped:0 overruns:0 carrier:2 
           collisions:0 txqueuelen:1000  
           RX bytes:1513874 (1.5 MB)  TX bytes:122279 (122.2 KB) 
           Interrupt:251  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
  
 ra0       Link encap:Ethernet  HWaddr 00:15:af:e7:13:af   
           inet6 addr: fe80::215:afff:fee7:13af/64 Scope:Link 
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:3232 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:2081 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:679994 (679.9 KB)  TX bytes:0 (0.0 B) 
           Interrupt:19  
 

 iwconfig
 

 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA" 
           Mode:Auto  Frequency=2.462 GHz  Access Point: Not-Associated    
           Bit Rate:1 Mb/s    
           RTS thr:off   Fragment thr:off 
           Link Quality=100/100  Signal level:-50 dBm  Noise level:-97 dBm 
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
  
 pan0      no wireless extensions.
 

 lspci
 

 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
 00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
 00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
 00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) 
 00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) 
 00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
 00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
 00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
 00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
 00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
 00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
 00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) 
 00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
 01:00.0 Network controller: RaLink RT2860 
 03:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)

---

