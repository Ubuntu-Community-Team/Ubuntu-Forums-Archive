---
title: "Intellinet 150n not working on Ubuntu 9.10"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by JonathanAnon on 2010-08-03
Hi guys, having trouble getting this Intellinet 150n working on Ubuntu 9.10... 

Use the same device with my windows PC (going back and forth between the two) so I'm sure that a) the Intellinet 150n is working and b) Both wireless (with essid: "stone", channel 6 and no security) and DHCP are  working on the router. Once the windows box receives IP settings from DHCP it connects to the Internet without any problems. 

When I plug the Intellinet 150n device in to the USB of the Ubuntu box, I get the following outputs:

   **ifconfig wlan0**
    wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:86:3a:22  
  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
  
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:1000 
  
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
  
  
  **iwconfig wlan0**
  wlan0     IEEE 802.11bgn  ESSID:"stone"  
  
            Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
  
            Tx-Power=12 dBm   
  
            Retry  long limit:7   RTS thro: off   Fragment thr: off
  
            Encryption key: off
  
            Power Management: on
  
            Link Quality:0  Signal level:0  Noise level:0
  
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
  
            Tx excessive retries:0  Invalid misc:0   Missed beacon
 [B]
iwlist wlan0 scan[/B]    wlan0     No scan results
  
  

When I run the **dhclient wlan0  **command it does not get an ip address, and even when I configure the wlan0 with IP address, mask and gateway, I still not ping the IP address of the router. 

Any help apprecited.. thanks.

---

