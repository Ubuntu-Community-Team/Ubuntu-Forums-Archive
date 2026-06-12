---
title: "No wireless connection Mythbuntu 11.04"
date: 2011-07-07
forum: Mythbuntu
---

### Post by childe joseph on 2011-07-07
OK here we go. I have a Rosewill RNX-N150PC Wireless Lan. The card's not listed in the Network Manager. To the Terminal..."iwconfig" yields the following:

lo            no wireless extensions

eth0        no wireless extensions

wlan0      IEEE 802.11bgn  ESSID:off/any
              Mode:Managed   Access Point:Not-Associated    Tx-Power=20 dbm
              Retry long limit:7   RTS thr:off    Fragment thr:off
              Power Management:off

So I can see my wireless card here. When I issue command:

:~$ iwconfig wlan0 essid NETGEAR ap any

I get back:

Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted

Any help would be appreciated.

---

