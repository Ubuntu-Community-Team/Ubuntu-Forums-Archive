---
title: "Wireless stops on two ubuntu laptops, works on windows laptop"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by Lenny212 on 2011-07-08
I have two ubuntu 11.04 laptops that today stopped working with my home wifi, but my windows laptop works fine.
These same ubuntu laptops connect fine to iPhone wifi hotspot.
I am very confused - can you help?

---

### Post by nick4554 on 2011-07-08
I have had similar problems with my netbook and wifi. What sort of computer do you have, and what happens when you try to connect?

open a terminal and type:
```

iwconfig

```

and post the results here. 

It seems to me that wifi will either work with your linux distro or it wont. there dosent seem to be allot you can do about it.

---

### Post by dasan on 2011-07-08
You can give a try by searching for restricted drivers

---

### Post by Lenny212 on 2011-07-08
Hi Nick4554,
I have an Asus EeePC and Lenovo T60. Both run ubuntu 11.04 and until today were working fine on home wifi. Windows machine works on same home wifi. Both ubuntu laptops work on iPhone hotspot.

I typed in iwconfig while using iPhone hotspot - the result is:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"iLenny212"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: FE:2B:61:1F: D6: 0B   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=70/70  Signal level=-21 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11   Missed beacon:0

---

### Post by Lenny212 on 2011-07-08
Thanks dasan, how do I search for restricted drivers.
Also, do you know why it would suddenly stop working?

---

### Post by Lenny212 on 2011-07-08
I should clarify, wifi appears connected according to icon at top right of screen, I can connect and disconnect, I just have no internet access

---

### Post by ScousaJAY on 2011-07-09
hi lenny

i also had a problem today on a EeePC, model 1005HA, and its sounds like a similar problem to yours.

take a look at my thread and see if this helps you, its worth a shot :) :

look at post 1 and 5
[http://ubuntuforums.org/showthread.php?t=1800188](http://ubuntuforums.org/showthread.php?t=1800188)

---

### Post by Lenny212 on 2011-07-13
Thanks ScousaJAY, I will check when I get home tonight

---

### Post by Lenny212 on 2011-07-15
Thanks again ScousaJay, it seems my issue was similar to yours. My ISP helpdesk upgraded the modem/router firmware and problem has gone away.

---

### Post by dasan on 2011-07-17
Please mark the thread as solved

---

