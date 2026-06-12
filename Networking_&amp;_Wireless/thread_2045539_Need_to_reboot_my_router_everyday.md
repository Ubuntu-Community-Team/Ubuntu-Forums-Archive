---
title: "Need to reboot my router everyday"
date: 2012-08-21
forum: Networking &amp; Wireless
---

### Post by Thorak04 on 2012-08-21
Hi,

First I'm new to Ubuntu.  I did my best to look through the forums and make sure I couldn't find a solution to my problems but didn't.  I'm fairly techsavy, but not enough to figure this one out by myself.

Here's the problem.  Every now and then I need to reboot my router, otherwise Ubuntu (12.04) won't connect to the wifi.  It will try to connect to my network and after ~30sec will say it didn't work and ask me for the password.  It just does this over and over again.  To get around it, I need to turn the computer off, unplug the router, wait 1-2min, replug it, wait 30sec and then open the computer.

I know the problem is within Ubuntu since I had the same setting with Windows7 without problems and that my phone and my gf netbook (Win7 starter) do not have any problems.

I also noticed that this situation happens after my computer has been offline for a certain amount of time (not sure how long, but probably something like 4-5h or more).  If I let it on and connected, it stays connected for days.  But if I close it for the night, then I need to reset the router in the morning.

At first I thought that maybe my router couldn't give enought IP addresses, but I checked and it has 99 available addresses with a 1 week lease. So it can't be it.

I tried to reboot the network with :
sudo /etc/init.d/networking restart

But it didn't work.  

Here are my ifcongig and iwconfig when it can't connect to the network :

mathieu@MauriceLaMorue:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1f:16:aa:b1:66  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:996 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:996 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:79472 (79.4 KB)  TX bytes:79472 (79.4 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:99:b1:62  
          inet6 addr: fe80::217:c4ff:fe99:b162/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:282 (282.0 B)  TX bytes:8029 (8.0 KB) 

mathieu@MauriceLaMorue:~$ iwconfig 
lo        no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          
eth0      no wireless extensions.

And here they are after rebooting the router and being connected :

mathieu@MauriceLaMorue:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1f:16:aa:b1:66  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:5503 (5.5 KB)  TX bytes:5503 (5.5 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:99:b1:62  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::217:c4ff:fe99:b162/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:245 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:124638 (124.6 KB)  TX bytes:31658 (31.6 KB) 

mathieu@MauriceLaMorue:~$ iwconfig 
lo        no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:"Tofu ninja"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0D:88:BC:0A:A5   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:2  Invalid misc:176   Missed beacon:0 

eth0      no wireless extensions. 

Hope you guys can give me a hand! 

Math

---

