---
title: "Cannot connect to internet with wireless"
date: 2006-05-15
forum: Networking &amp; Wireless
---

### Post by ahlandberg on 2006-05-15
I finally got my Netgear wireless card (WG311 v3) installed yesterday. Needed to use ndiswrapper and the driver files from the card's driver CD to fix the problem.

It seems that the card is correctly configured. I am using a wireless router which  runs DHCP. Therefore, I selected DHCP as connection type when configuring my ath0 connection. It even detected all wireless networks in my area and offered me to choose one to connect to. So all the settings seem to be ok.

When I now try to ping any other machine on the network (even my own one), it says: network unreachable. Also, when starting Firefox I cannot connect to the internet.

Who has got an idea what's wrong here?

Thanks in advance!

Cheers, Anders

---

### Post by DJ Scribblinni on 2006-05-15
To help in figuring out your problem do a ```
ifconfig
``` in the terminal and post what the output up here.  Do the same for ```
iwconfig
```

Another thing, if you used WEP, just make sure you typed the key in correctly.  And something that messed me up, is to make sure you either selected the Hexidecimal, or Plain (ASCII) correctly...  But that is only if you have assigned a WEP key for the network.

---

### Post by ahlandberg on 2006-05-16
Here is the output from the commands 'ifconfig' and 'iwconfig':

'ifconfig'
-------------------------------------------------------------
ahlandberg@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:508716 (496.7 KiB)  TX bytes:508716 (496.7 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:8B:AA:25
          inet6 addr: fe80::20f:b5ff:fe8b:aa25/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:ca010000-ca01ffff

ahlandberg@ubuntu:~$



'iwconfig'
-------------------------------------------------------------
ahlandberg@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11FH  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm
          RTS thr:2346 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-71 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11  Invalid misc:7   Missed beacon:0

ahlandberg@ubuntu:~$

---

### Post by DJ Scribblinni on 2006-05-16
From your output your computer is obviously not connected to the router, hence Access Points reads all zeros, and you do not have an IP address for wlan0. 

 My next thought would be to check the Properties you have for the wlan0, check the ESSID.  (Unless you get connected to that router, you won't get any IP address; even assigning a static IP won't even help you)

Other than that I seriously have no clue...

---

### Post by slightly72 on 2006-05-17
I'm a bit confused. You said:

> Therefore, I selected DHCP as connection type when configuring my ath0 connection. It even detected all wireless networks in my area and offered me to choose one to connect to. So all the settings seem to be ok.


Does that mean you're not configuring wlan0, but some other plugin card ath0? Maybe that's the problem. Have you tried to restart the networking after configuring wlan0 (/etc/init.d/networking restart)? You might also want to look in /etc/networking/interfaces, to add a line "auto wlan0" to start the interface automatically when (re)booting. Otherwise, everything seems to be ok from what you've described.

---

