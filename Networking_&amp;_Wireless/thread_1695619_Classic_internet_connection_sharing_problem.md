---
title: "Classic internet connection sharing problem"
date: 2011-02-26
forum: Networking &amp; Wireless
---

### Post by RedRoss on 2011-02-26
Hello people :)

I believe a lot of people had this issue at least once, I solved it on my previous laptop, but now there just seems to be too many loose ends to catch the actual problem.

[B]Things I am trying to do:
[/B]Share my internet connection (connected to eth0), through my wireless (wlan0), preferably with some encryption

**Things that work:**
I have internet connection on my laptop.

[B]Things that don't work:
[/B]Can't create an ad-hoc network (my laptop doesn't connect to any network it creates, except wpa one, but then its greyed out in network manager and other laptops can't see it)
Connecting with other laptops to my ad-hoc network(obviously)
Sharing the internet (obviously)


Any help would be appreciated. Thanks and have a nice day ;)

Some info:
```

wlan0  Link encap:Ethernet  HWaddr 70:f3:95:e2:36:eb  
          inet6 addr: fe80::72f3:95ff:fee2:36eb/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53837 (53.8 KB)  TX bytes:0 (0.0 B)
          Interrupt:19 

wlan0  Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level:0 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I understand that a lot of people are busy with all the alphas of 11.04, but maybe some wireless guru would like to try to crack this configuration nut? :)

---

