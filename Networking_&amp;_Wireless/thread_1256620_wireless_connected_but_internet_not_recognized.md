---
title: "wireless connected but internet not recognized"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by beartofear on 2009-09-02
Hi everyone, I'll warn you from the start I'm not exceptionally knowledgeable but I'll try and be as informative as I can to get help. Right now Knetwork Manger in Kubuntu 8.04 is showing that I'm connected to the wireless network in the apartment, but I can't access the internet.  I can however connect with no problem in Windows so I don't believe I'm looking at a hardware issue.

I have a Gateway MT6828 laptop with an Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)network controller which should be supported from the list I found.   

iwconfig gave the following:  

iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"default"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point:    
          00:0D:88:3E:9D:87
          Bit Rate=11 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B
          Power Management: off
          Link Quality=87/100  Signal level=-45 dBm  Noise  
          level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid 
          frag:0
          Tx excessive retries:0  Invalid misc:0   Missed 
          beacon:0


From what I can tell, I am able to ping the IP address apparently assigned to the laptop, but I'm unable to ping a private ip (I tried the ubuntu forums as suggested in another thread).  I get an "unreachable host" message. 

Anyway, I'd appreciate any help/ideas I can get. 

Thanks!

---

### Post by dbalascak on 2009-09-02
Can you post the output from
 *netstat -rn*.

---

### Post by beartofear on 2009-09-03
Here is the output from netstat -rn


Kernel IP routing table
Destination   Gateway    Genmask     Flags   MSS Window  irtt Iface
192.168.0.0   0.0.0.0  255.255.255.0   U      0 0          0 wlan0
169.254.0.0   0.0.0.0  255.255.0.0     U      0 0          0 wlan0
0.0.0.0     192.168.0.1   0.0.0.0      UG     0 0          0 wlan0

---

### Post by beartofear on 2009-09-03
I'm sorry if that last bit was jumbled as I had trouble formatting it all in the message.  Also, I'm really hoping the assistance can keep coming.  I'd love to use linux full-time, but being able to connect to wireless is essential for me.

---

### Post by dbalascak on 2009-09-03
If you can ping your default gateway 192.168.0.1 as well, the the problem may be DNS. Are you getting an IP address by DHCP or setting a static IP.  DHCP should supply a DNS server.  You need to configure a DNS server if the IP is  static.  Your DNS server will probably be 192.168.0.1.

---

### Post by beartofear on 2009-09-04
It should be set up to be DHCP. 

I will try to ping the gateway as soon as I get the chance.  

Thanks for the help thus far!

---

