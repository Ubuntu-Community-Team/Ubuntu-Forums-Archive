---
title: "Enable Wireless Radio on IBM Thinkpad R51? (Ubuntu 10.04)"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by Callaleia on 2010-08-02
I'm experimenting with Ubuntu 10.04 on this laptop, an IBM Thinkpad R51.  This will be step 1 in the long process of trying to get the wireless to work.  The computer's main OS is Windows XP.  I should add that I've never used Ubuntu before, so I really don't know what I'm doing.

Normally the wireless radio is enabled using the Fn-F5 key combo, which works under Windows but Ubuntu doesn't recognize these key mappings. 

Ubuntu does seem to "see" the adaptor.  The "iwconfig" command shows this:
>           eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0For the record, the wireless adaptor is:
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

I'm sure there must be some simple way to fix this, but I'm not sophisticated enough to follow the logic of the older posts where folks have discussed these wireless radio switches...

Any advice/direction would be appreciated.

---

