---
title: "weak wireless"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by Rainbowsix on 2009-09-01
I have a Gigabyte GN-WP01GS, but my connection is unbearably slow.

Here is my iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Skooter"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:F0:F7:46:A1   
          Bit Rate=1 Mb/s   Tx-Power=7 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=72/100  Signal level:-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


I did not update the drivers, as I don't know how to.

---

### Post by w00ly on 2009-09-01
I had a similar issue and yea it probably does have something to do with the drivers. The default drivers that came with the OS were slow, set the bit rate to 1mbit like yours (or 36,000mbit/s according to the plasmoid) and had a low signal quality (and the link light didnt blink). Unfortunately after setting up ndiswrapper and installing the proper drivers from linksys, I couldnt get anyone  on here to respond as to why it wouldnt pull an IP.

Eventually I just gave up because installing drivers shouldnt be this difficult, nor take longer than a day to install (or 2 or 3 for that matter), and simply installed the DD WRT firmware on a spare router, set it on "bridged client" mode and now I have properly functioning 54mbit wireless device in ubuntu

---

### Post by Rainbowsix on 2009-09-02
I found the answer from searching on Google.

add **iwconfig wlan0 rate 54M** into _/etc/rc.local_ before the exit line

---

