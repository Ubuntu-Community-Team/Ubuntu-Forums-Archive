---
title: "Wireless + Toshiba Satellite L305-SP5806R"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by _georgios_ on 2009-02-10
I get the wired network, and when I connect a wireless usb, it gets the signal, without it, doesn't get it, please help. :D

p.s. cant play my music.....someone?

---

### Post by superprash2003 on 2009-02-10
well for music you could use totem player.. certain codecs maybe required for totem.. for which internet connection is required.. post output of **iwconfig** from the terminal and output of **iwlist scanning**

---

### Post by _georgios_ on 2009-02-10
thanks, I'll try them....those codes you gave me... what are they for?

anyone with more ideas, will gladly read them

---

### Post by superprash2003 on 2009-02-11
iwconfig shows which interface supports wireless
iwlist scanning lists wifi networks aorund ( to see if your card is able to scan for networks)

---

### Post by _georgios_ on 2009-02-22
iwconfig, i got:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"2WIRE450"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:3F:13:AA:E9   
          Bit Rate=54 Mb/s   Tx-Power=19 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=62/100  Signal level:-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


and iwlist:

Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 

o.o?

---

