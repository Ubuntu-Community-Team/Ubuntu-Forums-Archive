---
title: "Slower speeds after upgrade to 2.6.28-13-generic"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by ideaplan9 on 2009-06-23
Wireless no longer functioning at maximum speed after upgrading from 2.6.28-11-generic to 2.6.28-13-generic.  I had previously used the jaunty-backport modules to get my speeds at maximum, but after the update, my up/down speeds have decreased again.  The problem now exists in both the *11 an *13 kernels.

I have tried the following:
1. Installing old backport modules - After loading them up, Network Manager recognizes my access point, but it does not accept or can't connect to it despite it given my WEP key.
2. Reverting back to 2.6.28-13-generic - problem still exits.

Any suggestions, on how to fix this?  As I understand there is already a bug report for this, but they haven't been working on it.  It would be nice for a change to have wireless on Linux work someday.

Extra Information:
```
04:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
```[html]wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 99:99:99:99:99:99   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-15 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/html]

---

