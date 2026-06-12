---
title: "Sharing Wifi in Ubuntu 11.04"
date: 2011-08-29
forum: Networking &amp; Wireless
---

### Post by samanosuke1983 on 2011-08-29
Hi there...

I have an issue i would like to discuss in this forum..

Sharing Internet Connection in Ubuntu 11.04 Nathy Narwal

I've been searching and reading a lot of documents and posts by the users about this, and i have not found any solution.

First i was using Win7, i was connected to the internet via Wifi with Atheros Wireless card i have in my laptop.

I installed Connectify to share my wifi connection and it was 100% functional: 

[CENTER]I was connected via wifi and sharing internet via wifi with connectify (hotspot), and i got no problems.[/CENTER]


But now i installed ubuntu 10.10, and upgraded to 11.04, i was having problems with the wifi connection but it is now solved..

Now ive been reading that its not possible to share the connection via hotspot if i am not connected by ethernet, and i say "how is this possible, windows can via hotspot (connectify) and Ubuntu can't? i cant believe it...

so i want to ask the community, what do you know about this matter?

because i would like to set my laptop in a hotspot, but still connected to internet via wifi...

gus@NaVi:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"INFINITUM405569"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:9F:E1:DD:36   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:17   Missed beacon:0

---

### Post by Feilin on 2011-08-29
I have exactly the same problem!

I found that it's possible to create a bridge, which allows for this kind of sharing, but I personally didn't really make it that far since I'm not a that experienced user. Hopefully someone can come to the rescue and explain things in a comprehensive manner...

I'm also not quite sure what card is in my laptop, but it's an Acer Aspire 5738ZG.

---

### Post by northd_tech on 2011-08-29
Here are some resources about Internet Connection Sharing (although I've always had several old 'obsolete' 802.11b/g WiFi routers handy and have gone the "hardware" route when necessary in the past):

Internet Connection Sharing
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Howto Share internet connection 
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

Sharing Internet Connection in Ubuntu
[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

How to Share a Wi-Fi Internet Connection in Ubuntu
[http://www.ehow.com/how_6865144_share-wi_fi-internet-connection-ubuntu.html](http://www.ehow.com/how_6865144_share-wi_fi-internet-connection-ubuntu.html)

How to Share a WiFi Internet Connection in Ubuntu [Method #2]
[http://www.ehow.com/how_7199711_share-wifi-internet-connection-ubuntu.html](http://www.ehow.com/how_7199711_share-wifi-internet-connection-ubuntu.html)

Sharing internet connection from windows to linux?
[http://answers.yahoo.com/question/index?qid=20110814182753AALI5OO](http://answers.yahoo.com/question/index?qid=20110814182753AALI5OO)

---

### Post by northd_tech on 2011-08-29
> **Feilin said:**
> 
I'm also not quite sure what card is in my laptop, but it's an Acer Aspire 5738ZG.

You can figure out the hardware question by posting the output from these terminal commands (although you might want to move to a different thread if you have hardware issues once determined):

```
lspci -nnvv | egrep 'etwork|thernet|ireless'
lsmod
sudo lshw -C network
ifconfig
iwconfig
lsusub
```

---

