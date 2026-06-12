---
title: "300Mbps Wireless USB on 150Mbps Router getting only 50Mbps speed"
date: 2013-03-03
forum: Networking &amp; Wireless
---

### Post by Thee on 2013-03-03
Hey

I need some help, I know Wireless speeds are lower in real world then advertised, but I really expected at least 100Mbps ...

My hardware:
D-Link DIR-600 (with latest firmware)
D-Link DWA-131 Wireless N USB adapter

My router supports up to 150Mbps, and the USB adpter 300Mbps, so the speeds should be good, but I'm only getting around 50Mbps (on Ubuntu, on Windows I get around 40Mbps)
The distance from the router to the USB adapter is like 1 meter. And there are no objects in between, except my desk.

So regardless of the OS, Im getting really low speeds. Anyone got any tips, because all I got on google search is that wireless sucks.
My router settings are attached.

Thanks

[ATTACH=CONFIG]239730[/ATTACH]

---

### Post by TheFu on 2013-03-03
Wifi sucks.  There are lots of issue with it. Interference can be a big one. That is highly localized.  Antenna design and deployment is more complex than most people appreciate.  Being a few inches off of the broadcast cneter for an antenna can make huge differences.  Also, each vendor many not implement the "standard" in the same way, so they all slow down.  The number of devices on the network effectively halves the bandwidth and whatever the slowest device connect is becomes the upper limit on bandwidth for everyone.  Don't use a microwave and any 2.4Ghz cordless phones nearby either.

Why do you have it set to high power?  That messes with the SNR negatively.  Also, why not let it auto select the best channel and speed?  I see you are force N-only - THAT is good.

What is the bandwidth limitation of USB2?  Isn't is 40Mbps .... and that is the theory, so in reality, it becomes somewhere south of 30Mbps.  Or is that MBps?

I know that my wifi-N wireless card inside my laptop was the cheapest one and doesn't even support 75Mbps. I should have paid the $15 for an upgraded version, which would have gotten me to 300Mbps.

I've never been impressed with d-link.  Then again, I've never been impressed with most wifi except Ubiquiti WAPs.

I'd also point out that greater speeds only matters for your internal LAN. Most broadband connections are 30Mbps or less and most internet servers will throttle fast connections to 1-2Mbps to be fair with all their users.

Wifi sucks.

---

### Post by Thee on 2013-03-03
I know the speed is as slow as the slowest client, but I only have this  one connected, rest of the computers are connected via ethernet and I  would connect this one too if I had more ethernet slots on the router,  and a switch I dont wanna buy yet when I have this wifi adapter laying  around.

> Why do you have it set to high power?  That messes with the SNR  negatively.  Also, why not let it auto select the best channel and  speed?  I see you are force N-only - THAT is good.

Power I did not change, I think it was set like that by default. What should i choose? Medium or Low?
Ill try with auto settings and see where that gets me, but I think it wont matter much.

> I'd also point out that greater speeds only matters for your internal  LAN. Most broadband connections are 30Mbps or less and most internet  servers will throttle fast connections to 1-2Mbps to be fair with all  their users.

Actually I have a 50Mbps internet connection, so with speeds that this wifi adapter gives me, I'm not even capping my internet speed :( It goes up to 52mbps on ethernet. And I was thinking of getting 100mpbs internet connection in the future...

Thanks for the reply!

EDIT: Channel set to Auto / Transmission rate set to Auto / Power set to Low = speed is 25Mbps now ...

---

### Post by tgalati4 on 2013-03-03
Install iperf.  Run iperf -s on one desktop machine and iperf client on the wireless to get some statistics.

I normally get 20 MB/sec using wirelss-G, but when netflix is streaming in another room it drops:

tgalati4@Mint14-Extensa ~ $  iperf -c tubuntu2 -w 1024k -i 2 -t 20
------------------------------------------------------------
Client connecting to tubuntu2, TCP port 5001
TCP window size:  256 KByte (WARNING: requested 1.00 MByte)
------------------------------------------------------------
[  3] local 192.168.1.103 port 48497 connected with 192.168.1.114 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 2.0 sec  2.12 MBytes  8.91 Mbits/sec
[  3]  2.0- 4.0 sec  2.50 MBytes  10.5 Mbits/sec
[  3]  4.0- 6.0 sec  3.25 MBytes  13.6 Mbits/sec
[  3]  6.0- 8.0 sec  2.75 MBytes  11.5 Mbits/sec
[  3]  8.0-10.0 sec  2.75 MBytes  11.5 Mbits/sec
[  3] 10.0-12.0 sec  2.50 MBytes  10.5 Mbits/sec
[  3] 12.0-14.0 sec  3.25 MBytes  13.6 Mbits/sec
[  3] 14.0-16.0 sec  3.38 MBytes  14.2 Mbits/sec
[  3] 16.0-18.0 sec  3.00 MBytes  12.6 Mbits/sec
[  3] 18.0-20.0 sec  2.75 MBytes  11.5 Mbits/sec
[  3]  0.0-20.1 sec  28.4 MBytes  11.8 Mbits/sec

Reverse the connection and go from the desktop to the wireless to see if there is a difference.

With all of the physical, electrical, and software layers, it's amazing that any of this stuff works at all.

---

### Post by TheFu on 2013-03-04
> **Thee said:**
> Actually I have a 50Mbps internet connection, so with speeds that this wifi adapter gives me, I'm not even capping my internet speed :( It goes up to 52mbps on ethernet. And I was thinking of getting 100mpbs internet connection in the future...

The total available internet bandwidth helps, but very few servers on the internet will push data that fast. Most will throttle users to 1-2Mbps.  OTOH, being able to have 30+ connects that are **each **throttled to 1-2Mbps is pretty great.  I had a really fast connection like yours a few years ago, but it didn't make much real difference, so I dropped back to a 12/3 connection and got more public IPs instead.

Could you run similar tests with exactly the same equipment over wired ethernet? Perhaps there is something else getting in the way, like a slow HDD?

Sorry that I'm not much help.

---

### Post by Thee on 2013-03-04
Here are the results:

```

Desktop > WIFI


[  3] local 192.168.0.104 port 40646 connected with 192.168.0.101 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 2.0 sec  7.25 MBytes  30.4 Mbits/sec
[  3]  2.0- 4.0 sec  6.75 MBytes  28.3 Mbits/sec
[  3]  4.0- 6.0 sec  5.25 MBytes  22.0 Mbits/sec
[  3]  6.0- 8.0 sec  6.25 MBytes  26.2 Mbits/sec
[  3]  8.0-10.0 sec  6.38 MBytes  26.7 Mbits/sec
[  3] 10.0-12.0 sec  4.88 MBytes  20.4 Mbits/sec
[  3] 12.0-14.0 sec  5.50 MBytes  23.1 Mbits/sec
[  3] 14.0-16.0 sec  4.75 MBytes  19.9 Mbits/sec
[  3] 16.0-18.0 sec  4.50 MBytes  18.9 Mbits/sec
[  3] 18.0-20.0 sec  5.12 MBytes  21.5 Mbits/sec
[  3]  0.0-20.1 sec  56.8 MBytes  23.7 Mbits/sec




WIFI > Desktop


[  3] local 192.168.0.101 port 37479 connected with 192.168.0.104 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 2.0 sec  7.75 MBytes  32.5 Mbits/sec
[  3]  2.0- 4.0 sec  7.75 MBytes  32.5 Mbits/sec
[  3]  4.0- 6.0 sec  7.75 MBytes  32.5 Mbits/sec
[  3]  6.0- 8.0 sec  8.12 MBytes  34.1 Mbits/sec
[  3]  8.0-10.0 sec  8.25 MBytes  34.6 Mbits/sec
[  3] 10.0-12.0 sec  8.00 MBytes  33.6 Mbits/sec
[  3] 12.0-14.0 sec  8.50 MBytes  35.7 Mbits/sec
[  3] 14.0-16.0 sec  8.12 MBytes  34.1 Mbits/sec
[  3] 16.0-18.0 sec  7.75 MBytes  32.5 Mbits/sec
[  3] 18.0-20.0 sec  7.38 MBytes  30.9 Mbits/sec
[  3]  0.0-20.0 sec  79.5 MBytes  33.3 Mbits/sec


-----


Desktop > WIFI (This time WIFI disabled and connected via ethernet)

[  3] local 192.168.0.104 port 40654 connected with 192.168.0.101 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 2.0 sec  22.5 MBytes  94.4 Mbits/sec
[  3]  2.0- 4.0 sec  22.5 MBytes  94.4 Mbits/sec
[  3]  4.0- 6.0 sec  22.5 MBytes  94.4 Mbits/sec
[  3]  6.0- 8.0 sec  22.4 MBytes  93.8 Mbits/sec
[  3]  8.0-10.0 sec  22.5 MBytes  94.4 Mbits/sec
[  3] 10.0-12.0 sec  22.4 MBytes  93.8 Mbits/sec
[  3] 12.0-14.0 sec  22.5 MBytes  94.4 Mbits/sec
[  3] 14.0-16.0 sec  22.4 MBytes  93.8 Mbits/sec
[  3] 16.0-18.0 sec  22.5 MBytes  94.4 Mbits/sec
[  3] 18.0-20.0 sec  22.4 MBytes  93.8 Mbits/sec
[  3]  0.0-20.0 sec   225 MBytes  94.1 Mbits/sec




WIFI > Desktop (This time WIFI disabled and connected via ethernet)

[  3] local 192.168.0.101 port 37485 connected with 192.168.0.104 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 2.0 sec  22.6 MBytes  94.9 Mbits/sec
[  3]  2.0- 4.0 sec  22.4 MBytes  93.8 Mbits/sec
[  3]  4.0- 6.0 sec  22.5 MBytes  94.4 Mbits/sec
[  3]  6.0- 8.0 sec  22.4 MBytes  93.8 Mbits/sec
[  3]  8.0-10.0 sec  22.5 MBytes  94.4 Mbits/sec
[  3] 10.0-12.0 sec  22.5 MBytes  94.4 Mbits/sec
[  3] 12.0-14.0 sec  22.4 MBytes  93.8 Mbits/sec
[  3] 14.0-16.0 sec  22.5 MBytes  94.4 Mbits/sec
[  3] 16.0-18.0 sec  22.4 MBytes  93.8 Mbits/sec
[  3] 18.0-20.0 sec  22.5 MBytes  94.4 Mbits/sec
[  3]  0.0-20.0 sec   225 MBytes  94.2 Mbits/sec

```

So I think we can rule out every hardware as a possible problem, except the WIFI.

---

### Post by TheFu on 2013-03-04
> **tgalati4 said:**
> Install iperf.  Run iperf -s on one desktop machine and iperf client on the wireless to get some statistics.

I normally get 20 MB/sec using wirelss-G, but when netflix is streaming in another room it drops:

This is due to multiple devices sharing the same frequencies.  A rough estimate for the impact is to reduce the theoretical bandwidth by 50% for every device on the channel.
0 Dev = 150 Mbps
1 Dev = 75 Mbps
2 Dev = 37.5 Mbps
3 Dev = 18.75 Mbps

So, with 2 devices connected to a wifi-150 AP, both can expect throughput of about 38Mbps. 
We aren't talking active use, just being connected impacts.

Of course, you can deploy TDMA APs (like Ubiquiti) and get higher throughput, but most home users and small businesses will not bother.

Could there be other wifi devices on your network?  Smartphone, tablet?

---

### Post by Thee on 2013-03-04
No, absolutely nothing is running on WIFI except that one.

I have:
2 desktop PCs
1 Raspberry Pi
1 Laptop
1 NAS device
And except that one desktop, everything else is connected via ethernet.

---

### Post by TheFu on 2013-03-04
What do your neighbors have that could be interfering? If you live on less than 3 acres, interference can be a problem.

My neighbors don't seem to understand that there are only 3 non-overlapping wifi-G channels in the USA.  1, 6, 11.  Every other channel overlaps with 1 or 2 of those, so picking anything other than those is just going to slow everyone down.

---

### Post by pierceTN on 2013-03-04
If you only have 50 Mbps going into your wifi router, then your not going to get any more out of it over wifi. If it is interference, than you will be having intermittent issues as well.

Try plugging directly in to your Ethernet cable that is plugged into the internet port in your router, then run a few speed tests. (like, speedtest[dot]net) then unplug, and connect to your wifi router through wireless and run a few, then compare the speed between the hardwired, and wireless. If they are about the same (give or take about 10%) then it is not going to be a wireless problem.

also, make sure you have a good connection signal to your router, it could be that your router is out of range, (i.e. distance, brick wall, etc...).


And like others have said, it could be interference from other radios on the same frequency.This will most likely happen when you live in a neighborhood. If you see what channels other routers are on then you can set yours to a different channel to avoid interference. 



Hope that helps some,


-Pierce

---

### Post by TheFu on 2013-03-05
> **pierceTN said:**
> If you only have 50 Mbps going into your wifi router, then your not going to get any more out of it over wifi. If it is interference, than you will be having intermittent issues as well.  He's doing local transfers, as stated in the OP. WAN bandwidth doesn't matter.

> **pierceTN said:**
> Try plugging directly in to your Ethernet cable that is plugged into the internet port in your router, then run a few speed tests. (like, speedtest[dot]net) then unplug, and connect to your wifi router through wireless and run a few, then compare the speed between the hardwired, and wireless. If they are about the same (give or take about 10%) then it is not going to be a wireless problem.
He did this already AND posted results above.  To, From, wifi, ethernet.  Done.

> **pierceTN said:**
> also, make sure you have a good connection signal to your router, it could be that your router is out of range, (i.e. distance, brick wall, etc...).
Somehow, I think he told us he was in the same room. What distance that is, I don't know, but line of sight and as long as he's 5ft away, that should be enough.  Too close CAN be an issue.

> **pierceTN said:**
> And like others have said, it could be interference from other radios on the same frequency.This will most likely happen when you live in a neighborhood. If you see what channels other routers are on then you can set yours to a different channel to avoid interference. 
Based on what he's shared already, I'm hopeful that checking other wifi channels already happened, but it would really matter most in a city or apartment setting.  My neighbors and I area ll on half-acre lots, so as long as we don't choose bad channels, the outside interference is less than 10% of my issue.  The OP hasn't said what his neighborhood is like.

At this point, if it isn't interference due to an apartment location or local microwave and cordless phone, I'd be looking at the wifi drivers and would move the wifi card/dongle to a different PC to see if that helps nail this down.

I'd also make sure that the SSID was being broadcast - some chips don't work as fast with that disabled.

---

### Post by Thee on 2013-03-05
Like TheFu already said, I already did all the tests and wireless is the problem, now we only need to figure out why is wireless the problem.

The best results I am achieving with the router settings set to what I showed in my 1st post. I didn't try every possible channel, I only tried a few and channel 13 gave the best results.
I live in apartment and I'm picking up about 5 other wireless signals from the neighbors. Is there a way for me to see which channels my neighbors are using?

And again, my wifi adapter and router are 1 meter apart (3 feet) with only a wooden desk in between.

Speed test:

ETHERNET:
[[IMG]http://www.speedtest.net/result/2552248088.png[/IMG]]("http://www.speedtest.net")

WIFI
[[IMG]http://www.speedtest.net/result/2552255533.png[/IMG]]("http://www.speedtest.net")

I would be able to live with this internet speed, but when it comes to transferring large files to my NAS, 50Mbps less makes a huge difference.

---

### Post by Thee on 2013-03-05
Ok I did
```
iwlist wlan0 scan
```

to find out channel numbers in use, and they are:

1, 2, 6, 10 and mine on 13

---

### Post by TheFu on 2013-03-05
> **Thee said:**
> I live in apartment and I'm picking up about 5 other wireless signals from the neighbors. Is there a way for me to see which channels my neighbors are using?
Yes, my router running Tomato has a site survey capability. That's the easy way.  I don't have any Linux machines using wifi here, but he Windows laptop has a vendor-specific wifi tool that shows all the channels used with signal strengths.

Channel 13?  On 2.4Ghz, we only have channels 1-11 in the USA.  That is just as well, since only channels 1, 6, 11 do not overlap.

> **Thee said:**
> And again, my wifi adapter and router are 1 meter apart (3 feet) with only a wooden desk in between.

Did you look up the antenna broadcast characteristics yet?  3 ft might be too close. There is a sweet-spot for distance from the antenna, based on how the antenna is positioned.
[https://apps.ubuntu.com/cat/applications/precise/wifi-radar/](https://apps.ubuntu.com/cat/applications/precise/wifi-radar/) is for Linux (never used it)
[http://www.makeuseof.com/dir/wifi-analyzer-the-best-wifi-channel/](http://www.makeuseof.com/dir/wifi-analyzer-the-best-wifi-channel/) is an android app to find wifi signals.

---

### Post by Thee on 2013-03-05
> **TheFu said:**
> 
Did you look up the antenna broadcast characteristics yet?  3 ft might be too close. There is a sweet-spot for distance from the antenna, based on how the antenna is positioned.

No I didn't, I'll try to find out .. always thought the closer, the better ...

Meanwhile, channel list looks good to me:

[ATTACH=CONFIG]239794[/ATTACH]


EDIT: Ok I extended the distance from the router to the adapter about 8 feet, and there is absolutely no change in speed. I tried various positions and thats about as far as I can separate them... I guess I could attach the adapter to my laptop and try again... but I doubt it would be any better :(

---

### Post by bellaseem on 2013-03-05
Can I see the full output of these two commands please?

```
iwlist wlan0 scan
```

```
iwconfig 
```

Also, the name of the network you're trying to connect to if you're not connected to it

---

### Post by Thee on 2013-03-05
```

wlan0     Scan completed :
          Cell 01 - Address: FC:75:16:A2:34:AE
                    ESSID:"thee"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.472 GHz (Channel 13)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD130050F204104A00011010440001021041000100
                    Signal level=100/100  
          Cell 02 - Address: 1C:C6:3C:2A:EA:E2
                    ESSID:"EasyBox-2AEA60"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2020050f20401000050f2020000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Signal level=47/100  
          Cell 03 - Address: 74:31:70:62:4B:53
                    ESSID:"WLAN-624B41"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD910050F204104A00011010440001021041000100103B0001031047001000000000000000030000743170624B531021000B436F72706F726174696F6E10230009564756383533394A5710240008312E32372E3030301042000A4A3134313034383530311054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084103C000103
                    Signal level=56/100  
          Cell 04 - Address: 24:65:11:ED:4E:B4
                    ESSID:"FRITZ!Box Fon WLAN 7270"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac020100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD6A0050F204104A0001101044000102103B00010010470010D7E90B01A44A56AC2FD7ED116524B44E1021000341564D10230009465249545A21426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020188103C000103
                    Signal level=92/100  
          Cell 05 - Address: 5C:D9:98:1F:4D:78
                    ESSID:"HT_AP0"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Signal level=7/100  
          Cell 06 - Address: 00:23:08:26:D3:E2
                    ESSID:"EasyBox-26D352"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD8A0050F204104A00011010440001021041000100103B000103104700100000000000000001100000230826D3E21021000B44534C2D45617379426F78102300094152563435323050571024000931302E30322E3031311042000A523833393135343234321054000800060050F20400011011001144534C2D45617379426F78204120363031100800020004
                    Signal level=46/100  
          Cell 07 - Address: 1C:C6:3C:4A:8A:F3
                    ESSID:"ALICE-WLAN43"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Signal level=42/100  
          Cell 08 - Address: 00:26:4D:26:20:A9
                    ESSID:"EasyBox-262001"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2020050f20401000050f2020000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Signal level=46/100  
          Cell 09 - Address: 7C:4F:B5:4B:79:F8
                    ESSID:"WLAN-4B7945"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD130050F204104A0001101044000102103C000103
                    Signal level=7/100  
          Cell 10 - Address: 00:24:FE:AD:49:4E
                    ESSID:"Alice-WLANQJ"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac020100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=23/100  
          Cell 11 - Address: 08:86:3B:6D:9E:76
                    ESSID:"belkin.e76"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B2860108863B6D9E76103C000101
                    Signal level=42/100  

```

```

wlan0     IEEE 802.11bgn  ESSID:"thee"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.472 GHz  Access Point: FC:75:16:A2:34:AE   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by bellaseem on 2013-03-05
Ok I noticed this in the iwlist command output:

```
wlan0     Scan completed :
          Cell 01 - Address: FC:75:16:A2:34:AE
                    ESSID:"thee"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.472 GHz (Channel 13)
                    Encryption key:on
                    Bit Rates:[COLOR=#ff0000]1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s[/COLOR]
[COLOR=#ff0000]                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s[/COLOR]
[COLOR=#ff0000]                              24 Mb/s; 48 Mb/s[/COLOR]
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD130050F204104A00011010440001021041000100
                    Signal level=100/100  
```

What's in red is the rates that the network named "thee" supports... Notice the rates of the network? It doesn't show 150Mb/s , so I'm guessing your router is not set to N mode (it's g from this output), try setting it to N only mode from its settings. (I might be wrong on this though if iwlist doesn't show rates higher than 54Mb/s... ). Also, concerning the distancing of the adapter from the router, I think the distance from the router is perfect seeing that the link quality and signal level are both 100/100.

Also, if your USB adapter has a configuration utility, you might want to check to set it to N mode only also...

EDIT: I think iwlist doesn't show a 150 Mb/s rate, at least I can't find any online... Also I noticed that your router is already in N-only mode...

---

### Post by bellaseem on 2013-03-05
[COLOR=#000000][FONT=Arial]Found this, I think it's appropriate here:

"The fact that you have strong signal but not at least the 65mbps data rate suggests that your client is limiting itself to *_G mode_* operation for some reason. The most common reasons are:[/FONT][/COLOR]

[LIST=1]
[*]The router is not set to do N on its 2.4GHz radio.
[*]Your router or your client is configured to use WEP or TKIP (WPA1) encryption, not AES-CCMP (WPA2). WEP and TKIP, as implemented by most Wi-Fi gear, is not fast enough to keep up with N rates, so the 802.11n spec disallows using those modes with 802.11n connections. To get N rates, you have to use AES-CCMP or no encryption.
[*]Your AP (or I suppose your client) does not have QoS (802.11e, WMM) enabled. The 802.11n spec requires QoS."
[/LIST]


So basically I would suggest going into your router's settings and trying to enable QoS (also do this for the client). Also check your router and adapter to force them to use N mode only from the wireless settings. If that doesn't work, then try using no encryption or WPA2 and see how things go...

Also this is relevant if you have the DD-WRT firmware on your router (or if you want to consider getting it [I have it and I would suggest it]:

"[COLOR=#000000][FONT=Arial]Then, if you really want to give your client a chance at max performance, you could enable 40MHz-wide channel mode on the 2.4GHz radio of your AP. It uses the lion's share of the 2.4GHz band and thus is quite likely to interfere with other things (and be interfered with by other things), but if you want a chance to get 150mbps instead of just 72.2mbps, you'll need to enable 40MHz channel mode. Try to at least lock your AP to one end of the band though, by picking either channel 1 or channel 13 (11 in North America)"


[/FONT][/COLOR]

---

### Post by Thee on 2013-03-05
But why does it say 150Mbps here then?

[ATTACH=CONFIG]239797[/ATTACH]

The router is set N only right from the beginning. I dont know how can I set the adpter to N only and if it can be set, but I didnt notice any option like that when I reboot to Windows with vendor drivers running.

---

### Post by bellaseem on 2013-03-05
You might be able to set the mode in windows by opening the Network and Sharing Center, then clicking Change Adapter settings , then right clicking your adapter and selecting properties, then clicking configure then advanced. (I have the realtek utility for my usb adapter and it allows me to specify B or G from the utility...) I'm not sure why the rate says 150Mbps, did you set it manually by typing in " iwconfig wlan0 rate 150M " ? 

Other than that, I have no ideas. Good luck! :)

---

### Post by Thee on 2013-03-05
No I didn't set it to manually, it was like that when I connected.
Just for the sake of the test, I disabled the wireless password, so that shouldn't be the problem, but the speed remains the same.

I'll reboot to Windows now..

---

### Post by tgalati4 on 2013-03-05
The bottom line of this thread is not to believe what is printed on the box, or what sticker is placed on the product.  Only testing in your environment is what matters.  Everything else is marketing or pure speculation.  As far as the Network Dialog box, you could look at the code and see where the speed variable is pulled from.  There are a lot of impediments to getting high wireless speed.  Your best bet is to run Cat6 wires to several convenient locations around the house and be satisfied with 92-94 megabit/sec speeds.

---

### Post by Thee on 2013-03-05
> **tgalati4 said:**
> The bottom line of this thread is not to believe what is printed on the box, or what sticker is placed on the product.  Only testing in your environment is what matters.  Everything else is marketing or pure speculation.  As far as the Network Dialog box, you could look at the code and see where the speed variable is pulled from.  There are a lot of impediments to getting high wireless speed.  Your best bet is to run Cat6 wires to several convenient locations around the house and be satisfied with 92-94 megabit/sec speeds.

I agree, wired is the best way. But like I mentioned earlier, because I dont have any more ethernet ports on my router, before I buy a network switch, I wanted to try my luck with the hardware that I already had.

Ok, in Windows, it shows something else... First, I cant select N only, and second, It shows 72/144Mbps, who knows why ...

[ATTACH=CONFIG]239799[/ATTACH]

---

### Post by Thee on 2013-03-05
> **bellaseem said:**
> 
Also this is relevant if you have the DD-WRT firmware on your router (or if you want to consider getting it [I have it and I would suggest it]:

"[COLOR=#000000][FONT=Arial]Then, if you really want to give your client a chance at max performance, you could enable 40MHz-wide channel mode on the 2.4GHz radio of your AP. It uses the lion's share of the 2.4GHz band and thus is quite likely to interfere with other things (and be interfered with by other things), but if you want a chance to get 150mbps instead of just 72.2mbps, you'll need to enable 40MHz channel mode. Try to at least lock your AP to one end of the band though, by picking either channel 1 or channel 13 (11 in North America)"
[/FONT][/COLOR]

You think DD-WRT firmware would help?
BTW, I cant select 40MHz channel mode only, only options are 20MHz or 20/40Mhz

---

### Post by bellaseem on 2013-03-05
I think you might want to check it out, the link here says that it's ridiculously easy to install (and easy to uninstal too):

[http://dd-wrt.com/wiki/index.php/DIR-600](http://dd-wrt.com/wiki/index.php/DIR-600)

also, the link will give you more details about the firmware for dir-600 which I think you should read (it's not as well supported at other routers, so that might be a disadvantage)...

My experience with dd-wrt is that it performs better than the stock firmware (at least for my router, also a d-link, and it has many more options, and is less glitchy).

Oh and you can overclock your router too (haven't tried this)

EDIT: Just read about someone using DD-WRT to set the encryption to WPA2-AES and the banding to 40Mhz using dd-wrt and getting over 135Mbps after having a speed similar to yours... So I guess the solution is a firmware change for your DIR-600? here:
[http://www.dd-wrt.com/phpBB2/viewtopic.php?t=76461&postdays=0&postorder=asc&start=15&sid=84d52a4cb84eb525e20d112acec704ec](http://www.dd-wrt.com/phpBB2/viewtopic.php?t=76461&postdays=0&postorder=asc&start=15&sid=84d52a4cb84eb525e20d112acec704ec)

---

### Post by Thee on 2013-03-05
Well after trying to update the firmware to dd-wrt, I get the following message "Invalid image file. Please select the correct image file and upload it again."

Google shows that that only Revision B2 is supported and my says Bx so I think I can't use that firmware on my router. So I guess I'm back to square one. 
[http://www.dd-wrt.com/phpBB2/viewtopic.php?t=140065&postdays=0&postorder=asc&start=0](http://www.dd-wrt.com/phpBB2/viewtopic.php?t=140065&postdays=0&postorder=asc&start=0)

Anyone got a tip on which my next router should be? Preferably not very expensive? Might change this one for a Gigabit one in the future. Until then, anyone got any more ideas I could try?

Thanks

---

### Post by tgalati4 on 2013-03-05
I would spend some time on the dd-wrt forums and see what folks are using, then ask on that forum for a recommendation that will give you decent wireless-N performance.

Good, Fast, Cheap.  Choose two.

---

### Post by TheFu on 2013-03-06
> **tgalati4 said:**
> I would spend some time on the dd-wrt forums and see what folks are using, then ask on that forum for a recommendation that will give you decent wireless-N performance.

Last fall I swapped out my 7+ yr old trusty Buffalo router for a new, shiny GigE N-300 router.  I had researched DD-WRT compatibility and was excited when it arrived.  I flashed the new firmware and started to configure it for my subnets and multiple public IPs .... before actually connecting it to the WAN link. Everything was great and seemed stable.  The WiFi part was only slightly interesting - I'm a CAT6/1000base-tx guy.

All was configured, so swapped out the old router for the new one.  No WAN connection. Dead WAN port.  Swapped cables. Dead. No light.  LAN stuff was working just fine.  WiFi was working ... er ... good enough - 75Mbps (thanks to a cheap N adapter in a laptop).  Fine.  More research showed that dd-wrt was missing the ability to enable the WAN port. Seems the OEM firmware has it disabled, then enables it after all the firewall filter rules are active.  This prevents leaks through the router after a reboot.  However, the WAN port default is disabled and dd-wrt never enables it.

More research on the dd-wrt forums ... and an odd group of steps were discovered to get the WAN port enabled.
* flash OLD vendor firmware
* flash specific German vendor firmware (with bug that resets WAN port open)
* flash old DD-WRT
* flash desired/current DD-WRT

My HS German is extremely rusty, but I managed. Seemed like a long way to go to get a few more GigE ports and WiFi-N (that I can't really use).  I already had a d-link AP with B, A bands.  Remember 72Mbps 802.11a?  

If I were you, I'd go and buy a $20 8-port TRENDnet GigE switch (I have this, it replaced a burned out d-link) and be done.  A new router is not required to get GigE speeds on the LAN if all the GigE capable devices are directly connected to that switch (not the router) and on the same subnet (usually a /24).  650Mbps - easy.  You can slowly move over devices as you replace the 10/100 cards with GigE NICs, though the switch will handle 10/100/1000 fine.  Your current router is working for the WAN bandwidth you have.

---

### Post by Thee on 2013-03-06
> **TheFu said:**
> 
If I were you, I'd go and buy a $20 8-port TRENDnet GigE switch (I have this, it replaced a burned out d-link) and be done.  A new router is not required to get GigE speeds on the LAN if all the GigE capable devices are directly connected to that switch (not the router) and on the same subnet (usually a /24).  650Mbps - easy.  You can slowly move over devices as you replace the 10/100 cards with GigE NICs, though the switch will handle 10/100/1000 fine.  Your current router is working for the WAN bandwidth you have.

Oh I did not know that, thanks for the info! :) I always assumed if the router is limited to 100Mbps that the switch connected to the router would also be limited to that speed. But now that I think about it, it does make sense :P

Ok, well thank you all for your help, at least I learned some things here even tho I didnt solve the wifi problem :)
I guess I'll try to find a cheap Gigabit switch then.

Thank you!

EDIT: erm... where is the "Mark as solved" button?

---

### Post by TheFu on 2013-03-06
> **Thee said:**
> Oh I did not know that, thanks for the info! :) I always assumed if the router is limited to 100Mbps that the switch connected to the router would also be limited to that speed. But now that I think about it, it does make sense :P
That is what the netmask is all about. Things inside the same subnet talk directly without any routing.  Of course, you'll need GigE network cards.  I've been burned a few times with the $12 cards only pushing 200-300 Mbps, so I spurge for the $18 Intel PRO/1000 cards now.  650+Mbps consistently.

I will say that my switch is an 8-port TrendNet-Green and my router is an old wifi-G 10/100 Buffalo. All connections are CAT6, except a few long runs to other parts of the house, which are CAT5e. I can't see any difference in speed between these.

> **Thee said:**
> Ok, well thank you all for your help, at least I learned some things here even tho I didnt solve the wifi problem :)
I guess I'll try to find a cheap Gigabit switch then.
We're all learning here - constantly.

> **Thee said:**
> EDIT: erm... where is the "Mark as solved" button?
Check under Thread Tools menu at the top.  At least that is where it was pre-update. ;)

---

### Post by Thee on 2013-03-07
Yea it was there before the update, but it's not there any more.

Anyway, I hope my NIC's are good, they are integrated ones. But they are Gbit, I ordered some Netgear switch, should arrive in few days, and then we will see.

---

