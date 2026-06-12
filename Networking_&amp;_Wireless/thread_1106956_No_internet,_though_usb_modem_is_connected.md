---
title: "No internet, though usb modem is connected"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by u_walker on 2009-03-26
Hi,

I have trouble with my three modem (Huawei E220). I have installed Ubuntu 2 weeks ago, but I just have sometimes an internet connection, though the blue or green light on the modem is always on, and the Ubuntu start page (with google search window) also always shows (and Network manager also shows the connection). 
So sometimes from the start page on, all pages seem to work fine, but I have to restart my computer about three or four times to make internet work. So its just not reliable.

So when internet doesnt work, firefox shows however the start page but it doesnt take me anywhere else.

What works also is  [http://74.125.67.100](http://74.125.67.100), which takes me to the google page, but same thing, on a bad day I just can get on the start or google page, but I cant do any searches and it doesnt show anything else.

I would appreciate if somebody could tell me how I can fix this.

Cheers

---

### Post by sammy_pal on 2009-03-26
Instead of using the network manager applet to connect, you can try using wvdial ( see this link - [https://help.ubuntu.com/community/DialupModemHowto/Huawei/E22]("https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220")0 ) or gnome-ppp (  [https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220/GnomePpp](https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220/GnomePpp) ).

---

### Post by superprash2003 on 2009-03-27
post output of **ifconfig** from the terminal...try changing your DNS servers to opendns- 208.67.222.222 and 208.67.220.220

For reference : [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

