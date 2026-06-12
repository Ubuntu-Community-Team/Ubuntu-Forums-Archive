---
title: "Hotspot is not visible on other devices (12.04 precise)"
date: 2012-05-10
forum: Networking &amp; Wireless
---

### Post by juliohm on 2012-05-10
I am trying to create a hotspot in my home ubuntu installation (12.04 Precise). The configuration seems OK and the hotspot is activated. However, the hotspot created by Ubuntu does not appear on other devices.

My iPhone can't see the hotspot. The same goes for my friend's Android device.

To create the hotspot, I used the standard GUI via

* System Settings > Network > Wireless
* Click "Start Hotspot"

Wait a few seconds and the notification appears informing the network was successfully configured. If I click the network icon in the top right corner of the screen, the hotspot is listed as connected. In the terminal, the network card even got an IP address

```
wlan0     Link encap:Ethernet  HWaddr NN:NN:NN:NN:NN:NN
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: NNN::NNN:NNN:NNN:NNN/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:345 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:91818 (91.8 KB)

```

Am I missing something here? I also remember trying this with Ubuntu 11.10 without any luck.

---

### Post by masterserver on 2012-05-17
I have exactly the same problem. I cannot figure out how can the WiFi hotspot work on Ubuntu. 

My results from ifconfig is 


```
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:10.34.113.114  Bcast:10.34.113.127  Mask:255.255.255.128
          inet6 addr: XXXX::XXXX:XXXX:XXXX:XXXX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:89418680 (89.4 MB)  TX bytes:3533396 (3.5 MB)
          Interrupt:55 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:997 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:178253 (178.2 KB)  TX bytes:178253 (178.2 KB)

wlan0     Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: XXXX::XXXX:XXXX:XXXX:XXXX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10563 (10.5 KB)

```

and my result from the iwconfig


```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"nikos-Inspiron-N5110"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: XX:XX:XX:XX:XX:XX   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
```



I get these results while i have activated the wifi hotspot function of Ubuntu. I am running Ubuntu 12.04 and my wireless card is Intel Centrino Wireless-N 1030.

Thanks in advance

---

### Post by tumutanzi.com on 2012-05-19
You need to do some setup work. Here is a detailed tutorial showing how to set up Ubuntu 12.04 laptop as WiFi hotspot (ad-hoc) to share wired internet: [http://tumutanzi.com/archives/8195](http://tumutanzi.com/archives/8195)

I have tried using this tutorial, and it works for my two laptops, iPad 2 and my Nokia 5800.

I think it should also works for iPhone.

---

### Post by masterserver on 2012-05-19
I did all this and I think all works fine. 
The thing is that i am trying to connect my android phone with this ad-hoc network and I realized that android devices are unable to detect ad-hoch networks by default. 

So my problem now is with my android phone. How can I make it to detect ad-hoc networks?

I tried this [[COLOR="DarkOrange"]http://forum.xda-developers.com/showthread.php?t=1489868[/COLOR]]("http://forum.xda-developers.com/showthread.php?t=1489868")
but it didn't work for me.

---

### Post by williantalvane on 2012-05-27
The same here. I have an HP dv6 with dual boot Windows 7 and Ubuntu 12.04. I already tried everything I found on the internet. Nothing works. It says that my network is connected but I cannot find it in my HTC Incredible 4 Android.

---

### Post by masterserver on 2012-05-27
Hi guys

I found a solution that works perfectly with my dual boot system with Ubuntu 12.04 and my HTC Sensation 4G. Maybe it will work for your systems too. Here is the solution

Step 1:

First you have to create a proper ad-hoc network in you Ubuntu in order to share you internet. Here is the tutorial on how to do this [http://tumutanzi.com/archives/8195](http://tumutanzi.com/archives/8195)


Step 2:

In this step now you need to make your android phone to detect this ad-hoc network and connect to it. Here is the second tutorial on how to do this [http://www.ce4arab.com/vb7/showthread.php?t=420240](http://www.ce4arab.com/vb7/showthread.php?t=420240)
This tutorial is a little bit tricky so if you have question just ask. 

Hope that was helpful

Thanks

---

### Post by pruthvi223 on 2012-10-15
me 2 having da same problem...did u find ny solution for this..if so plz help me out....

---

### Post by rtv_73 on 2013-08-15
I ran into the same problem. You need to make sure your network adapter support "Master Mode" (Access Point Mode). Here is a link with the information to check it out:
[https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)

[www.fishingforladies.com](www.fishingforladies.com)

---

### Post by juliohm2 on 2013-08-15
For what it's worth, I tested my network ca[FONT=arial]rd with [/FONT]**[FONT=courier new]sudo iwconfig wlan1 mode master[/FONT]** (as instructed in the link) and turns out my wifi adapter does not support the "master" mode.

```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.



```
So that's it for me.

Thanks for the help!

---

### Post by david-c-moffatt on 2014-06-17
Hold up.   You do not want to put your NIC in master mode.   That is for turning it into a hotspot.   The original post said he wanted to do ad-hoc. This is peer to peer connection.

---

