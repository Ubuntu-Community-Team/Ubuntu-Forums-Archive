---
title: "Really bizarre wifi networking problem"
date: 2012-01-27
forum: Networking &amp; Wireless
---

### Post by mililani on 2012-01-27
Hi folks,

I am running Ubuntu 10.10 with all the latest fixes.  Currently, I use an external USB wifi adapter called the Alfa Awus036NH.  Prior to that, I used the Alfa Awus036H.  The Alfa AWUS036NH uses a driver called "usb".  So far, it is working fine.  However, when I decide to switch to the Awus036H, it works fine for about 5-10 seconds, and then it's like an internal firewall goes up and I cannot get any HTTP traffic going.  I can't ping, do nslookups, or whatever. What is odd is that SMTP traffic SEEMS to be working.  My email alert applet shows new alerts, although, I can't be sure if that's just a red herring (perhaps it's cached locally). Ifconfig shows ip is configured correctly with dns and gateway.  The driver being used is called RTL8187.

So, does anyone know what is going on here?  This adapter USED to work.  I know this isn't a driver issue, because I can see wireless networks and get on them.  I just can't get outbound traffic.  Any ideas?

---

### Post by Bucky Ball on 2012-01-27
In the downloads section at the bottom of this page you find your card. There are Linux drivers for two of them. Try them out. Instructions for installation are included with the downloaded software.

---

### Post by mililani on 2012-01-28
I must be obtuse.  What download section?

---

### Post by Bucky Ball on 2012-01-29
Ha! Sorry, forgot to put the link in. Try the bottom of this page:

[http://www.realtek.com/search/default.aspx?keyword=RTL8187](http://www.realtek.com/search/default.aspx?keyword=RTL8187)

---

