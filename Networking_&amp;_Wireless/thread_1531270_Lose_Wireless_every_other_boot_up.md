---
title: "Lose Wireless every other boot up"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by reslider on 2010-07-14
Just installed 10.4 haven't used Ubuntu since 7.04. I was never really proficient with it but after that time I am def rusty so please bare with me. 

So every other time I boot up I either gain or lose wireless. Right now I have it, If I would restart I would not have, then restart again it will work fine. 

If I type in iwconfig now i get 
> 
tyler@weaksauce:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"u-verse"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1F:B3:24:75:49   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-25 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

when its not working I only get 

> tyler@weaksauce:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

I don't know what is changing every other boot cycle

I've been trying a few things and Im not sure what I typed in but I got back the response of something like 

Ignoring  unknown interface wlan0=wlan0

Any help is great, its not super vital because I know it will work, just a hassle having to boot up twice sometimes

---

