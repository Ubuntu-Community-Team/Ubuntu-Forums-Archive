---
title: "Help! My Realtek 8187 wireless card..."
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by zeezon1990 on 2009-01-03
I run Ubuntu 8.10 and Vista 32bit sp1 on my laptop. There is sth wrong with my realtek wireless 8187 card because In ubuntu I cann't surf internet when the wireless signal intensity is less than 30%. However in the same place when using Vista I can go surfing even though the wireless signal intensity is still 30%.

  I don't know why, Can you give me some suggestions. Thx and Thx again.:D

---

### Post by giantoz on 2009-01-03
try this:

[http://techii.wordpress.com/2008/12/23/solution-for-ubuntu-810-and-rtl8187b-wifi-problem-short-range-wifi/](http://techii.wordpress.com/2008/12/23/solution-for-ubuntu-810-and-rtl8187b-wifi-problem-short-range-wifi/)

---

### Post by zeezon1990 on 2009-01-05
The link you gave seems to be blocked...

:confused:

---

### Post by svaens on 2009-01-05
here's the text from the site. I was able to browse it no problems:


Recently, I installed Ubuntu 8.10 on my notebook which contains RTL8187B WLAN card. unlike previous versions of Ubuntu which don’t detect such card, 8.10 detected the card, and WLAN worked very well. But I noticed that the range of the WLAN is very short, and after very few meters from the router, there is no traffic.
 After some long search, here is the solution that worked with me:

1- gksu gedit /etc/rc.local

2- Add the following line to rc.local before exit 0

iwconfig wlan0 rate 5.5M fixed

3- Reboot

Of course there are some other solutions based on ndiswrapper or the modified RTL8187B driver, but I found the above solution powerful and easy and no big change happened in the system.

---

### Post by zeezon1990 on 2009-01-09
OK, I'll have a try and I hope it will work.


However I still wonder **whether the wicd has a effect on my card**. I removed Network-manager instead of Wicd.

---

