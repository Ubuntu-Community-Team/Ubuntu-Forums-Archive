---
title: "hostapd - Failed to create interface mon.wlan"
date: 2011-03-19
forum: Networking &amp; Wireless
---

### Post by Mindjigger on 2011-03-19
Hi guys,
I'm trying to make an AP with RTL8187L Wirelss USB card. I got a lot of obstacles till now. First was with getting Master mode. It works with the official driver on the RTL site.
Now I got the following:

"root@benga:~# hostapd /etc/hostapd/hostapd.conf dd
Configuration file: /etc/hostapd/hostapd.conf
Failed to create interface mon.wlan1.
nl80211 driver initialization failed.
root@benga:~# "

I appreciate any further suggestions and help.
Thanks in advance.
Regards.

---

### Post by flash63 on 2011-03-19
Hallo,
no AP/Master-Mode support for this driver possible

[http://www.linuxwireless.org/en/users/Drivers/rtl8187](http://www.linuxwireless.org/en/users/Drivers/rtl8187)
[http://www.linuxwireless.org/en/users/Drivers](http://www.linuxwireless.org/en/users/Drivers)

---

### Post by Mindjigger on 2011-03-19
Hi,
I don't believe that. See the following with rtl8187l:

wlan1     802.11bg  ESSID:"Penguin"  
          Mode:Master  Channel=5  Access Point: 00:C0:CA:41:F0:D9   
          Bit Rate=11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@benga:~#

---

