---
title: "Wireless connection often brakes"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by Kognit on 2010-04-27
Hi

I have a laptop ASUS k50IJ and when i am connected to internet (wireless connection) the connection often brakes so i have to reconnect and sometimes restart a computer so that the connection will work for some time (let's say 30-60 minutes, sometimes less). The connections most oftenly brakes when i download some movies,....

Any help!

---

### Post by Cabalbl4 on 2010-04-27
What sort of connection is established? Ad-hoc or infrastructure?
What device are You using to connect to? A router or other PC?

---

### Post by Kognit on 2010-04-27
Firstly, thank for reply.

It is infrastracture and i am using a wireless router.

My wireless driver is ath9k.

---

### Post by Cabalbl4 on 2010-04-27
I think there may be 3 issues:

1) Interference. Are any other devices running?
2) Driver problem. I did have a gleach on Ath5k with disconnects. Sometimes setting fragmentation threshold to 512 bytes helped me (sudo iwconfig wlan0 frag 512). The problem disappeared when I removed windows from pc I was connecting to and installed ubuntu over it.
3) Encryption problem. Some problems with WPA are reported... However, I never experienced any of them. Is unencrypted connection broken as often as the encrypted one is?

---

### Post by Kognit on 2010-04-27
> **Cabalbl4 said:**
> I think there may be 3 issues:

1) Interference. Are any other devices running?
2) Driver problem. I did have a gleach on Ath5k with disconnects. Sometimes setting fragmentation threshold to 512 bytes helped me (sudo iwconfig wlan0 frag 512). The problem disappeared when I removed windows from pc I was connecting to and installed ubuntu over it.
3) Encryption problem. Some problems with WPA are reported... However, I never experienced any of them. Is unencrypted connection broken as often as the encrypted one is?

There is no other devices running. 

What this fragmentation does and why to 512?

With unencrypted connections i have some troubled history. Today i have tried to connect to two unencrypted networks. With the first i couldn't connect, with the other i had more luck regarding connections, but i wasn't able to browse the web (i didn't have check the "work offline".

---

### Post by Cabalbl4 on 2010-04-28
Fragmentation is a way to send packets not in whole, but by parts. Setting fragmentation decreases speed (not much), but increases the chance for other side to get the packet. I've got best performance against disconnects when it was set to 512 bytes instead of auto (default setting).  

What does ```
dmesg
``` return when You fail to connect?

Btw, which network manager do You use? And can You post the output of ```
iwconfig
``` here?

---

### Post by Kognit on 2010-04-28
Actually, i found a page and have install the modules. So far so good - [click. ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474858")

Iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"SASO"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:60:19:9C:51   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-25 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Cabalbl4 on 2010-04-28
Well, it seems that the packets are going smoothly... No errors on recieve. Let's hope that the modules backports will work. However, if it fails, You may try another card driver and another network-manager.

---

