---
title: "wifi connection."
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by cloudbounce with LED's on 2009-04-05
hello to all,
I'm new to linux
this has most probably been put forward before but this computer
is so slow its quicker to ask a question then go through all the 
existing questions.

I've just had ubuntu 8.10 install by a tech ,he did it for me coz other work had to be done on the computer at the time.

When i got the tower home and connected it the wireless connection was there even though netcomm  doesn't support linux. 
after three days it disappeared (something i did wrong i guess) now i cannot get it back again.

In Editing wireless connection,
What is ssid and bssid, netcomm charge a $50 fee to give any assistance :(

also i get asked for key ring password which has not been set. 
if i need these to get my connection back how do i reset these?

---

### Post by superprash2003 on 2009-04-05
in your terminal type the following commands and post its output
1)iwconfig
2)ifconfig
3)iwlist scanning

---

### Post by cloudbounce with LED's on 2009-04-06
> **superprash2003 said:**
> in your terminal type the following commands and post its output
1)iwconfig
2)ifconfig
3)iwlist scanning

I might be wrong with the heading
I have a USB adapter and I am trying to connect to my wireless modem router. Sorry for the confusion. 

Here is my result-

alan@alan-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=18 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

alan@alan-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d4:9c:60:1f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8000 (8.0 KB)  TX bytes:8000 (8.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:60:64:1e:b3:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-60-64-1E-B3-38-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

alan@alan-desktop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

alan@alan-desktop:~$

---

### Post by superprash2003 on 2009-04-06
ubuntu seems to have recognized your card.. the last output says that wlan0 did not find any wifi networks around.. you have a wifi network around right?

---

### Post by cloudbounce with LED's on 2009-04-06
I have called this thread wifi connection. is that wrong?
I have  a 54 Mbps wireless USB adapter and i am trying to connect
to my wireless adsl modem/router.

For the first three day's after the install of ubuntu 8.10 the connection was there plus my neighbors wireless connection.
i could see the signal strength of my network.

---

