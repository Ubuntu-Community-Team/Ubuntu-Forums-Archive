---
title: "[SOLVED] iwconfig and result"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by Sbarton on 2008-12-22
Hi all! I am still having a problem connecting or configuring wireless connection. I know I have a Atheros AR5009 card in stalled. 
However, if I type iwlist in terminal I get the following
harry@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=23 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Now I know my card is Atheros?? Am I missing something or should I be doing something else? I am new to wireless! I can see other wireless connections and the above one. I am dual booting with Vista and have no problems using wireless with that as it picks up my BTrouter connection. Can somebody help me with this.
Thanks and regards

---

### Post by Sbarton on 2008-12-23
For what it is worth! I changed wireless channel in my router, which solved one problem. After this I typed 'iwconfig' again in terminal and now have the correct ESSID:name which is notas given above. Would this channel change have done this or is this weird!!
regards

---

