---
title: "Wireless card detected and on...No networks (SAYS: Wireless Disabled)"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by strujillo.jr on 2009-01-15
Hey so i have my wireless card working and everything but i cant get it to find my network and connect to it. I have tried this for the last two days spending almost 6 hours a day on it...But i have Dell and when i start it up the WiFi light is on, and the wifi is detected, but in the network manager thingy it shows grayed text that says

```

Wireless Networks
Wireless is Disabled
``` and when i right click there is a button that says ```
Enable Wireless
``` but you cant click on it cuase its all grayed and disabled. oh and when i do iwconfig it gives me this
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

---

### Post by utnubuuser on 2009-01-16
Don't know about the Dells, but on thinkpads  it's a Fn+F5 to enable/disable wireless.

I've seen several posts in the last few days about Dells having this problem.  If you can't find the posts any other way, try doing a advanced search with parameters for the last 4days + Dell.

---

### Post by superprash2003 on 2009-01-16
post output of
1)lshw -C network
2)iwlist scanning

---

