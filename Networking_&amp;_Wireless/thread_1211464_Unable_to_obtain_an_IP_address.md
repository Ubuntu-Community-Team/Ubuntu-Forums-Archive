---
title: "Unable to obtain an IP address"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by alasdairsim on 2009-07-12
I am using Ubuntu Juanty and wicd network manager.
 
When I try to connect to my wireless they network is found, I am authenticated but wicd cannot obtain an IP address.
 
LAN works fine. I am using WPA2 security.
 
Any suggestions?

---

### Post by apmcd47 on 2009-07-12
> **alasdairsim said:**
> I am using Ubuntu Juanty and wicd network manager.
 
When I try to connect to my wireless they network is found, I am authenticated but wicd cannot obtain an IP address.
 
LAN works fine. I am using WPA2 security.
 
Any suggestions?

I have no Linux experience of this but I have found 3 laptops running Win XP having problems with my Edimax router. They all had Intel wireless cards. I made sure my router had the latest firmware then contacted Edimax. They told me it was a known problem and I should upgrade the driver for the wireless card. Didn't work for me :-(

I ended up using a static address for my network.

This Vista laptop and a Sony PlayStation 3 work okay.

Andrew

---

### Post by alasdairsim on 2009-07-12
I can connect with a static IP, but no websites display.

---

### Post by Crafty Kisses on 2009-07-12
> **alasdairsim said:**
> I can connect with a static IP, but no websites display.
When you connect via static IP, can you view Google by opening Firefox and typing the following in the navigation bar?
```
74.125.67.100
```

---

### Post by alasdairsim on 2009-07-12
> **Codename said:**
> When you connect via static IP, can you view Google by opening Firefox and typing the following in the navigation bar?
```
74.125.67.100
```

No.

"The connection was refused".

---

### Post by Crafty Kisses on 2009-07-12
As root, run the following:
```
cat /etc/resolv.conf
```
Are there nameservers listed?

---

### Post by superprash2003 on 2009-07-13
are you connecting to a network which runs on a proxy server?

---

### Post by alasdairsim on 2009-07-13
> **Codename said:**
> As root, run the following:
```
cat /etc/resolv.conf
```Are there nameservers listed?

Yeah.

194.72.0.98
194.72.8.38

---

### Post by alasdairsim on 2009-07-13
> **superprash2003 said:**
> are you connecting to a network which runs on a proxy server?

No. It connects directly to the router.

---

### Post by Lampi on 2009-07-13
could you post the output of command 'iwconfig'?

---

### Post by alasdairsim on 2009-07-13
Iwconfig

>     lo        no wireless extensions.
     
   
  eth0      no wireless extensions.
     
   
  wlan0     IEEE 802.11g  ESSID:"BTHomeHub2-7FNH"  
              Mode:Managed  Frequency:2.432 GHz  Access Point: 00:24:2B:82:C4:C2   
              Bit Rate=24 Mb/s   Tx-Power:25 dBm   
              RTS thr:2347 B   Fragment thr:2346 B   
              Power Management: off
              Link Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
              Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
              Tx excessive retries:0  Invalid misc:0   Missed beacon:0
     
   
  pan0      no wireless extensions.
    

---

### Post by martinbaselier on 2009-07-13
How about pinging? 
in a terminal type
ping [ip-address]
Can you ping the ip of your router? 
Then try pinging the ip of your nameserver.
If that works try to use the google ip given above. 
Also try to ping [www.google.com](www.google.com) or some other website, 
to see if it returns an ip.

---

### Post by alasdairsim on 2009-07-13
> **martinbaselier said:**
> How about pinging? 
in a terminal type
ping [ip-address]
Can you ping the ip of your router? 
Then try pinging the ip of your nameserver.
If that works try to use the google ip given above. 
Also try to ping [www.google.com]("http://www.google.com") or some other website, 
to see if it returns an ip.

I tried to ping 194.72.0.98: "Destination host unreachable"

---

### Post by Lampi on 2009-07-13
@alasdairsim: iwconfig looks fine - now please follow [this tutorial]("http://ubuntuforums.org/showthread.php?t=202834") from iwlist scan

---

