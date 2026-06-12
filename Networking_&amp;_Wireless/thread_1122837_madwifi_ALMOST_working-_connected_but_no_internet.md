---
title: "madwifi ALMOST working- connected but no internet"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by twitch2197 on 2009-04-11
right now i'm repairing my wifi. it "broke" a while ago and i'm in the process of reconfiguring madwifi for it. I'm currently running the pclinuxos distro but i knew the ubuntuforums community would be able to help me out.
i've gotten this far: i can manually go in and connect to a network but i'll get a 0% signal. here's what iwconfig gives me:
```
[jordan@localhost ~]$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"08FX08016825"  Nickname:"localhost"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
so i'm connected to the network "08fx08016825" but getting nothing from it. what can i do to get internet access again?

---

