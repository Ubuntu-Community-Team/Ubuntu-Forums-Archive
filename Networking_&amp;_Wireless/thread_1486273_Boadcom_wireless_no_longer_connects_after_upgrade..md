---
title: "Boadcom wireless no longer connects after upgrade."
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by engmex on 2010-05-17
After upgrading to 10.04 on a Compaq laptop with AMD 64 I can no longer connect to the wireless router and get the error "bad password"  Using wicd.  The error seems to be conected with the following strange output from iwlist
wlan0     IEEE 802.11bg  ESSID:"\xE6\x9A\x8A\xFE\x1C\x0F(\xBDO$\xBC\x86N\\x11\xB3O\xFE:\xC8\xEE\xAE\xA9``Kn\xC3K\x88)1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
As you can see the ESSID and Mac addres are corrupted.  Here is the lspci info:
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
Any suggestions?

As a foot note I'm also have wireless networks issues on my desktop after upgrading and that is not using a broadcom card.

---

