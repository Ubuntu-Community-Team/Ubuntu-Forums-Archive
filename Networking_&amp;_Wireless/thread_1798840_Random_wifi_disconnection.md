---
title: "Random wifi disconnection"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by nick4554 on 2011-07-06
Hello,

I am having problems with my wifi. It connects to the internet fine for varying amounts of time (1 minute to 1 hour) and then cuts out on me. I have to reboot in order to get it to work. Also if i hibernate my netbook (close the lid) on reopening it the network is off and wont connect unless I reboot. 

I am running ubuntu 10.10 on my acer aspire one with an atheros ath9k wifi chipset. 

I have searched the internet for weeks and weeks trying to solve this issue. heres a bit of the back story:
last year had 10.10 working with similar problems. I ran 3 terminal commands from a website and it worked fine (dont remember the commands and cannot find the site again). this year 11.04 came out, and I upgraded. wifi didnt work, and I downgraded back to 10.10. the wifi still dosent work now. 

Ive tried turning the power management off:
```

sudo iwconfig wlan0 power off

```
Ive tried setting a fixed tx rate
```

sudo iwconfig wlan0 rate 54M fixed

```
Ive tried playing with the rmmod
```

sudo rmmod ath9k
sudo modprobe ath9k
sudo reboot

```

ive tested the netbook on different routers with the same results. ive tested other computers with the routers (windows) and they work fine. When the wifi is running and i run ping tests I get varing results with the average of 60% packet loss. I also get DNS errors randomly and have to F5 a few times before the page loads. 

The wifi isnt currently working, but im pluged in via ethernet to post this. 
the results of my ifconfig currently are:
```


nick@rvw:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:7b:d5:7c  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:fe7b:d57c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:14634 (14.6 KB)  TX bytes:17515 (17.5 KB)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25424 (25.4 KB)  TX bytes:25424 (25.4 KB)

wlan0     Link encap:Ethernet  HWaddr 90:4c:e5:08:19:e5  
          inet6 addr: fe80::924c:e5ff:fe08:19e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51947 (51.9 KB)  TX bytes:66841 (66.8 KB)

```

and of course the iwconfig is:
```


nick@rvw:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

help?

---

### Post by nick4554 on 2011-07-06
I just unplugged the ethernet connection and rebooted, and here is the iwconfig when the wifi is working

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Thomson7E6BC4"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 08:76:FF:7E:6B:C4   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

i have no doubt that it will disconnect within 30 minutes :frown:

---

### Post by nick4554 on 2011-07-08
Still having the problems with the wifi! 

Ive installed WICD but cant get that working properly. 

Help?

---

### Post by argybee on 2011-07-15
Sorry no solution nick4554 but I'm having exactly the same problem but with entirely different setup !!?? so I'm now watching your thread...

I'm on 10.04 (Mint) with RALink driver RT2860

>ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:22:43:43:00:71  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe43:71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77979 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12118871 (12.1 MB)  TX bytes:790462 (790.4 KB)
          Interrupt:16 



>iwconfig
wlan0     RT2860 Wireless  ESSID:"XXXXXX"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0F:B5:AE:A5:02   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:B837-137E-A7D1-5A90-5BC4-6775-2F
          Link Quality=100/100  Signal level:-64 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


...............

don't know if we can any see common issues through this

---

### Post by owiknowi on 2011-07-15
same troubles over here, with several notebooks and many distro's.
a while ago i did a complete reset of my router and connected my notebook to it with an ethernet cable. the ip address of the router should be in its manual or you can find it on the website of its manufacturer.

first gave it a new ssid, password (wpa2/psk, aes, WPA Group Rekey Interval:0), AP Isolation: off. also, and unfortunately, had to un-check the option Hide Access Point, and so on till i found the channel option.

the latter is by default set to auto, so the router is always checking for the channel with the best strength.

there was also a button with which i could scan for the best, and free, channel. i choose one of the two marked as having excellent strength, from the 13 available.

maybe this did the trick? have no more sudden disconnections since.

hope this helps.

also set change ip address (leased time) from 4 to 24 hours. this means afaik that the connected computer gets every 24 hours assigned a new ip address.

---

