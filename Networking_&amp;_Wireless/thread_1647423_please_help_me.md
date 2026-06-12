---
title: "please help me"
date: 2010-12-17
forum: Networking &amp; Wireless
---

### Post by ziedan on 2010-12-17
please any one can help me?
when i am writing iwconfig in the terminal i get all the parameters but i don't have the bit rate what can i do to get it??
here is what i have
i tried it on ubuntu 9.10 and 10.10
the same problem is occuring

ziedan@ubuntu:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"whitefii"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 66:5B:98:B0:6E:FB   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by spiky001 on 2010-12-17
Try ```
ifconfig
```

---

### Post by Kernelingus on 2010-12-17
No, ifconfig won't give you what you're looking for.

Your bit rate in most cases will be automatically set by your adaptor, but can be set manually with iwconfig.  In fact, iwconfif gives you a whole host of options when it comes to setting bit rates.

Learn them all here:

```
man iwconfig
```

Happy tweaking!

---

### Post by bkratz on 2010-12-17
> **ziedan said:**
> please any one can help me?
when i am writing iwconfig in the terminal i get all the parameters but i don't have the bit rate what can i do to get it??
here is what i have
i tried it on ubuntu 9.10 and 10.10
the same problem is occuring

ziedan@ubuntu:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"whitefii"  
          [COLOR=Red]Mode:Ad-Hoc[/COLOR]  Frequency:2.412 GHz  Cell: 66:5B:98:B0:6E:FB   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Did you mean to be in the Ad-Hoc mode?  Usually this is used between computers, not to an A/P.

---

