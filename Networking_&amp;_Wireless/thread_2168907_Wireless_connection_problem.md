---
title: "Wireless connection problem"
date: 2013-08-19
forum: Networking &amp; Wireless
---

### Post by Richard_OKeeffe on 2013-08-19
Hope I can be helped.
Complete noob to Linux here!
My wireless won't connect - it  asks for the password on the connection but won't establish a connection.
I've tried lots of things (badly), with zippo success.
Only thing I have picked up of note is there is massive amounts of noise showing on the system information program.

---

### Post by chili555 on 2013-08-20
Let's see what wireless device you have and see if we can tweak the driver settings. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Richard_OKeeffe on 2013-08-20
> **chili555 said:**
> Let's see what wireless device you have and see if we can tweak the driver settings. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.


Should have said its a usb wireless
Bus 001 Device 009: ID 050d:815f Belkin Components F5D8053 N Wireless USB Adapter v6000 [Realtek RTL8192SU]

result of iwconfig

> wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.


---

### Post by Richard_OKeeffe on 2013-08-20
sorry for the smilies

---

