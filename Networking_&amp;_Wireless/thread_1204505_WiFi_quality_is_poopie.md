---
title: "WiFi quality is poopie"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by kunnie on 2009-07-04
Every now and then, on Youtube for example, the video loads just fine, and suddenly it stops, without loading the vid fully. Also happens that, when downloading from the repositories, my connection seems "lost", just like in YouTube, and I have to cancel the download and start again. Otherwise, my connection is ok, signal is great and other sities work fine.

Any suggestion?

---

### Post by kerry_s on 2009-07-04
try typing> sudo iwconfig < in the terminal see if it looks right.
check your bit rate is right & what kind of quality you have.

---

### Post by kunnie on 2009-07-04
okay pal, here goes mine

wlan0     IEEE 802.11abg  ESSID:"Zaidenjaja"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:70:EE:CC   
          Bit Rate=11 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Encryption key:censured   Security mode: open
          Power Management: off
          Link Quality=85/100  Signal level:-48 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Wierd thing is, I got this problem after updating from 8.10 to 9.04. Also, I'm using a pc with Windows XP in the same room, and it works ok... so WTF is going on here :lolflag:?

---

### Post by kerry_s on 2009-07-04
first try increasing the bitrate to 54mb:

**sudo iwconfig wlan0 rate 54M**

hopefully that gives you full speed.

now your noise level is over a hundred, this could be caused by other networks being on the same channel as you.
do:

**sudo iwlist wlan0 scan**

look at what channels every 1 around you is using 6, 9 & 11 are the most common. now change the channel in your **router** to a channel that is not in use or has low use. hopefully that will reduce your noise and give you a clearer signal.

---

