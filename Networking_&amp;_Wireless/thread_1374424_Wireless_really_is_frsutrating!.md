---
title: "Wireless really is frsutrating!"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by tonyps on 2010-01-06
Toshiba Satellite A505D-S6958
AMD Turion-X2 64
Realtek RTL8192E wireless

I could really, really use some assistance with getting this to work under Ubuntu 9.10. I was provided with Linux drivers from one of the folks here, for which I again say many thanks!
I ran the make, make install per instructions, with no errors. Rebooted with no errors.
Wired connection works great, as has always been.
Wireless is dead as a door nail!!
**The wireless is seen as WLAN1 when running the iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     802.11bgn  Nickname:"rtl8192E"
          Mode:Managed  Access Point: Not-Associated   Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
**lspci sees the hardware as 8192(rev1) **
**02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)**
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
System-Administration-Network Tools- shows Network Device-Wireless Interface- WLAN1 as a wireless device that is installed but is inactive.
I am a Linux novice, pretty much at my limit with what else to do, look at...
I would greatly appreciate assistance from someone more experienced!
Thanks!
Tony ...

---

