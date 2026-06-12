---
title: "WLAN (rtl8191se) rate very slow"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by newwarrior on 2010-02-06
Hi,

i have installed my wlan card (rtl8191se).
I have no problem with that and it works.

But my Bitrate is very slow.
So I tested thinks like that:

```
malte@leppi:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  ESSID:"Marmelade"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.417 GHz  Access Point: 00:25:9C:27:A4:BB   
          Bit Rate=36 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=71/100  Signal level=-67 dBm  Noise level=-105 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

malte@leppi:~$ sudo iwconfig wlan0 rate 54MB
malte@leppi:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  ESSID:"Marmelade"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.417 GHz  Access Point: 00:25:9C:27:A4:BB   
          Bit Rate=36 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/100  Signal level=-66 dBm  Noise level=-104 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

malte@leppi:~$ 
``````
malte@leppi:~$ sudo iw reg set DE
nl80211 not found.
```I change the channel from my router.
but nothing works.
COuld you please help me?

---

