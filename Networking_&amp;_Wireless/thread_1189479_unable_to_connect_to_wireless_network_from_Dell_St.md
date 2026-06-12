---
title: "unable to connect to wireless network from Dell Studio 15 N laptop"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by minus_25 on 2009-06-16
I'm new to linux and would appeciate some help.  I am running Jaunty Jackalope and I used to always automatically connect to my wireless network everytime I logged in to the computer.  After one of the system updates, I am no longer able to connect to my wireless router.  I don't even see my network listed under "Wireless Networks" when I click on the network icon in the system try at the top of the desktop.  When I go to System -> Preferences -> Network Connections -> Wireless tab, I see my network listed 3 times (2 of them have the word "auto" in front of it.  I know my wireless router is working, because I was able to connect online with my Nintendo Wii.

I am running Jaunty Jackalope on a Dell Studio 15 N series laptop.

Here is the output from the "iwconfig" command:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.
/*******************************************************/
Here is the output from the "ifconfig -a" command:

eth0      Link encap:Ethernet  HWaddr 00:21:70:7a:a7:e1  
          inet addr:192.168.1.137  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fe7a:a7e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23977 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26889057 (26.8 MB)  TX bytes:4236128 (4.2 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:22:69:21:38:0e  
          inet6 addr: fe80::222:69ff:fe21:380e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1464 (1.4 KB)  TX bytes:1464 (1.4 KB)

pan0      Link encap:Ethernet  HWaddr be:d2:b4:d1:30:dd  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
/********************************************************/

Could someone please help me?

---

### Post by minus_25 on 2009-08-03
Never mind.  There is this little switch on the side of my laptop that looks like a tower transmitting a signal.  The switch must have accidentally been turned off.

---

