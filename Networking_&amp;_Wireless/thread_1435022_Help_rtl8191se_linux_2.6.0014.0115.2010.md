---
title: "Help rtl8191se_linux_2.6.0014.0115.2010"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by rapc0d on 2010-03-21
Excuse me... thanks  before,

Ubuntu 9.10 New User,

Yesterday I've install it on my notebook, but i dont understand why the wireless cant work..

i've try to install driver windows with ndiswrapper but cant work too, and now i've read this post [http://ubuntuforums.org/showthread.php?t=1425140&page=3](http://ubuntuforums.org/showthread.php?t=1425140&page=3) the problem same...

where i can download this file 
rtl8191se_linux_2.2.6.0014.0115.2010

because i want try like him(David)..

thanks
rapc0d,

---

### Post by chili555 on 2010-03-21
Please see post #1 of the link you gave. I notice that the file has been updated; a good thing. Be sure you have installed linux-headers-generic and build-essential. Also, when you extract the file, be sure to read and follow the readme.txt. If you get an error, stop and fix the error; post back if we can help you.

---

### Post by rapc0d on 2010-03-25
Yes, i,ve finish install and the result like this : (same with david)..
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```and then now, how i can scan the wireless access point... cz i want to try it's can connect or not ?
thanks chili :)

---

### Post by chili555 on 2010-03-26
Click the Network Manager icon at the top right and see networks; click yours and connect. If you do not see the icon, right-click the panel and select Add to Panel. Add a Notification Area. Please see attached.

---

### Post by rapc0d on 2010-03-26
many thanks chili :), i've finish success... i know... but my icon is lost... so i cant find...
and then after i've search on google, i can great! i use this command

```

rapc0d@rapc0d-laptop:~$ sudo iwconfig wlan0 essid GORANGO channel 11 mode managed

```

yes i've got it, can connect normaly :D

by the way, the davids problem are finishly friend...?

i think he was dont power on on this wifi adapter.. maybe ? :popcorn::popcorn:

---

