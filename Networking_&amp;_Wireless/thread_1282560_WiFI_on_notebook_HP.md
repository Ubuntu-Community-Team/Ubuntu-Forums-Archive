---
title: "WiFI on notebook HP"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by Hellrider13 on 2009-10-04
Hi. I have notebook HP 550 NA947EA. I've bought it specially for Ubuntu, while this model works perfect with Linux and there is no problems with WiFi at all. But I have it. My system is Ubuntu 9.04 and when I turn on the notebook, Network has to to be detect automatically. But Network Manager said that there is no Wlan networks. Then I installed Wicd, after uninstalling Network Manager, but Wicd says the same thing. Here is the log of wiconfig: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"My_Adhoc_Network"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

What can I do? Under Windows all works perfect. May be I need some drivers? Can you tell me what must I do? I work with Ubuntu only 3 days:) 
Sorry for my terrible English.

---

### Post by houstonbofh on 2009-10-04
Plug into a cable and run System --> Administration --> Hardware Drivers and see if you need a restricted driver.  I bet you have a Broadcom nic...

---

### Post by Hellrider13 on 2009-10-04
I have now switched on this proprietary driver for Wireless, rebooted, but nothing - as earlier, there is no connections. Here is also answer of ifconfig:

encap:Ethernet  HWaddr 00:24:81:6d:2d:1d  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:e4600000-e4620000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:db:11:08  
          inet6 addr: fe80::221:ff:fedb:1108/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I don't understand what I need - some drivers or something else - and it is the reason, why I don't know what to do next..:(

---

### Post by sendblink23 on 2009-10-04
erased

---

### Post by houstonbofh on 2009-10-04
I don't see any nic.  Do an lspci so we know what you have.

---

### Post by Bucky Ball on 2009-10-04
Is the blue light on indicating the card is? If so, System->Administration->Network, check your wireless properties and make sure the details in there match the details in your router or the details for your ISP or whatever (ESSID and WEP/WPA security key).

Your ESSID is currently 'My_Adhoc_Network' which probably isn't right but things seem to be happening. You should be concentrating on wlan0, forget the rest. You're just not associated to your access point or AP (your wireless router).

Another trick is get the details from your Windows wireless setup (ESSID, security key) and make sure they match in Ubuntu.

---

### Post by Hellrider13 on 2009-10-05
Bucky Ball, I tried to get all settings of wireless network from Windows and copy all to Ubuntu, but in Wicd there are not all these settings witch there are in Network Manager. And to install again Network Manager I need an Internet connection. For example I don't now where in Wicd enter a WEP-key or ESSID. In System-Administration-Network Tools there is not information about wireless networks. 

The problem is that I'm total new in Ubuntu but I want to use it. Please can somebody tell me step by step what to do? I've also installed driver from Linuxant but there is no effect.

---

### Post by Bucky Ball on 2009-10-05
Not Network Tools, Network. But hold on, if you installed Wicd it uninstalls Network Manager. Forget that. Don't know Wicd at all sorry. Never had call to use it. :(

---

### Post by Hellrider13 on 2009-10-05
By me there is only Network Tools in System-Administration:confused:

---

### Post by Bucky Ball on 2009-10-06
> **Hellrider13 said:**
> By me there is only Network Tools in System-Administration:confused:

Yea, like I said, wicd uninstalls Network Manager and I know nothing about wicd. Sorry.

---

