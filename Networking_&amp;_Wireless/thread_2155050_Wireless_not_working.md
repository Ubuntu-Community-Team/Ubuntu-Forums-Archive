---
title: "Wireless not working"
date: 2013-06-16
forum: Networking &amp; Wireless
---

### Post by frasnelli on 2013-06-16
Hello,
I recently upgraded my Samsung NF210 netbook to Ubuntu 12.04 LTS. I am experienceing (it looks like as many others) problems with the WIFI. I was reading through different threads and tried several suggested solutions, but I could not fix it. Can anybody help me?

What I have found out so far:
If I type

iwconfig 

I get:


lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"the love zone"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:01:CB:3F:7C   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


the command

lsmod | grep -e wl -e brcmsma

gives 


wl                   2906597  0 
cfg80211              178877  2 mac80211,wl
lib80211               14040  2 wl,lib80211_crypt_tkip



and finally
lspci -nn | grep 0280


results in:
05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)


Thanks a lot in advance
J

---

### Post by frasnelli on 2013-06-16
So, after having tried the whole evening by reading old threads, I finally gave up, and opened a thread on my own. Then I rebooted the computer, and ... the wireless works!!
So thanks anyways, but I do not need your assistance anymore

---

### Post by cluelesswonder on 2013-06-17
Coincidentally, I'm having the same problem and have rebooted my computer twice with no fix yet. I'm also running ubuntu 12.04 LTS
The same codes yield:

lo        no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
       eth0      no wireless extensions.

lsmod |grep -e wl -e brcmsma

wl                   2906597  0 
lib80211               14040  1 wl
cfg80211              178877  4 wl,ath9k,mac80211,ath

lspci -nn |grep 0280

02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

If I need to provide any more information, please let me know.

---

### Post by Techyte on 2013-06-17
This is a common ubuntu bug. An authentication error. I have heard suggestions of changing the password to a hex code or removing the password altogether. I can't say any of these work because I have never tried them. I use to have the same problem, I tried everything, even ndiswrapper, but eventually I just gave up and installed a wired connection. But one day it just worked. To this day I don't know what happended. I too would like to know how to fix this bug just in case I need to in the future.

---

