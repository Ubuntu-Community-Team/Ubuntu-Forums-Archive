---
title: "Wireless Speed Question"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by wah fun on 2010-04-16
Does anyone know how to get 802.11n connect speeds in ubuntu 9.04 64bit? My setup is as follows:
Belkin N150 Advanced Wireless Router (set to 802.11/b/g/n)(setting the router to 802.11n only does not work)
Belkin N150 Advanced USB Network Adapter (F6D4050 v2) uses ra2870 driver

I have tried compiling the native driver from ralink but no joy at all - couldn't even get it to work. So, I am using ndiswrapper with a windows 64 bit driver. But, my connect speed is only 54Mbps (which is only 802.11g). In windows (32 bit), the same setup gives me throughput of 135-150 Mbps.

Here is my iwconfig output:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"jujubean"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:75:74:AF:FB   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I would appreciate any feedback.

thx

p.s. I have tried ubuntu 9.04 32 bit and cannot get any wireless connection at all. Even ndiswrapper will not work with the windows xp 32 bit driver.

---

### Post by 2hot6ft2 on 2010-04-16
First set you wireless security to
WPA Personal
AES Encryption
Then check your speeds.
I had the info. on it saved but can't find it now.

EDIT: Must have lost the file but here's the jest of it.
In your routers setup.
First go to Manual Wireless Network Setup, change Security Mode to WPA Personal not WEP, AES Encryption and set 802.11 Mode: to N only (later you can change that to b,g,n it wont matter). After changing the Channel Width to 20/40mhz... uncheck Enable Auto Channel Scan, change the channel to one that isn't being used by others near you. 1, 6 or 11 are the best.

And the 5ghz band seems to work better for the simple fact that fewer people are using it.

---

