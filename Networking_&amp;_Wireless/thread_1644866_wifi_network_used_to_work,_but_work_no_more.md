---
title: "wifi network used to work, but work no more"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by francois.e on 2010-12-13
I am working with ubuntu (gnome) 10.10 maverick 64 bit on a HP pavilion 2713ca. I have installed the Broadcom sta driver for a BCM4328 wifi driver. After setting wpa security with my password, the wifi network worked for many weeks. However, in the last few days it doe not connect no more. 

I have tried to reinstall SSID. And I have checked to see if  eth1 was still there:

root@max-HP-Pavilion-dv2700-Notebook-PC:/home/max# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:14 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

What would you suggest?

---

### Post by francois.e on 2010-12-16
There seems to be a bug with ubuntu 10.10. This is the only OS that I used on my for many weeks.

However, I also have on a second partifion a vista installation that I did not touch for long. Booting vista, and trying to get the wifi work yielded the resolution of my problem. For some reason Ubuntu had turned off my wifi card. 

What is the reason for that?

---

