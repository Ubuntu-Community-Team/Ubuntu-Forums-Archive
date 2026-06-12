---
title: "Admin profile can access websites while standard user cannot"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by Yamipirogoeth on 2011-04-20
First off, since this seems like a networking issue I put it here, but if it should be somewhere else, the powers that be should definitely move it over.

I'm using Ubuntu 10.10 on Dell Presario M2000 I have made sure that all updates have been done.

As the subject states, the admin account (mine which I'm posting to the forum with right now) can access the internet and see webpages. The user account on this laptop (my underaged sister who my parents don't want full access to the computer) will not access any webpages, it just continually looks like its loading.

I have made sure the wireless card drivers are installed and activated.

Also, I ran iwconfig and ifconfig and here are their results

  	 	 	 	p { margin-bottom: 0.08in; }  Results of iwconfig
 

 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     IEEE 802.11bg  ESSID:"myqwest4137"   
           Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:7B:F7:39:DC    
           Bit Rate=54 Mb/s   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off  
           Link Quality=64/70  Signal level=-46 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 Results of ifconfig
 

 eth0      Link encap:Ethernet  HWaddr 00:c0:9f:ea:ea:4e   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:18 Base address:0xa000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:36 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:36 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:2160 (2.1 KB)  TX bytes:2160 (2.1 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr 00:14:a5:1f:02:42   
           inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0  
           inet6 addr: fe80::214:a5ff:fe1f:242/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:3633 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:1970 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:2889997 (2.8 MB)  TX bytes:286614 (286.6 KB)  
 
These were both run from the user account. At this point it looks like its connecting to the internet through the wireless card as I was also able to run the update manager through the user account and have it download the updates (after putting in my admin password of course).

So any help that I can get at fixing this would be helpful...or if you need me to run something else in the way of diagnostics.

---

### Post by An Sanct on 2011-04-20
In the network settings, make sure the checkbox "Available to all users" is checked. Its location is in the edit tab, where you edit the IP and other settings, in the first tab in the bottom.

---

### Post by Yamipirogoeth on 2011-04-20
Sorry An Sanct, I'm not sure where to find that. Would it be Network Connections? I looked there and there's nothing that I can change that matches that.

Though, I do have a program called "Nanny" that does parental control...and apparently I had switched off the wrong button. So, this is actually solved on account of my idiocy pressing the wrong button

---

