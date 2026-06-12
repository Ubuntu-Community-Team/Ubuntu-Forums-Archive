---
title: "Getting Master mode to work with Asus 167g v3"
date: 2011-03-12
forum: Networking &amp; Wireless
---

### Post by IHaveQuestions on 2011-03-12
I&#8217;m running Ubuntu 10.10 and try to get my wifi to work in master mode. The dongle is a Asus 167g v3 and I&#8217;m using the rtl8192SU driver. I can connect to a network or put the dongle in Ad-hoc mode without a problem. It&#8217;s when I try to put in master mode some problem occurs. When I do: ```
sudo iwconfig wlan1 essid test mode master
```

This is the output I&#8217;m getting:```
wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Master  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

The dongle is in master mode but it fails to assign a SSID. I also tried to set it up in /etc/network/interfaces but the result is always the same&#8230; No SSID

---

### Post by IHaveQuestions on 2011-03-16
Sorry but ka-bump

---

