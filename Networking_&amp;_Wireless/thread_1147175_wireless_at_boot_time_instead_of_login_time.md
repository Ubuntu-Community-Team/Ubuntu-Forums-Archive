---
title: "wireless at boot time instead of login time"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by feh on 2009-05-03
Hi folks.

I'm running xubuntu 9.04, and I have wireless configured so that it connects to my household wireless network. I'm using WEP encryption, and I don't broadcast the SSID.

Anyway, I've accomplished this through the nm-applet (a simply horrible piece of software). But, what I want is for the wireless connection to be established at boot time, not after I've logged in.

Is there any way to find out what commands nm-applet is running to establish the connection and somehow have them executed at boot time?

Thanks!

---

### Post by x22 on 2009-05-03
> WEP wireless at boot time

well, my method is to have a script called "wireless" in
/usr/local/sbin, then to call it from /etc/rc.local.  The
script is

ifconfig wlan0 up
iwconfig wlan0 essid chris
iwconfig wlan0 channel 11
iwconfig wlan0 mode managed
iwconfig wlan0 key 1234567890
iwconfig wlan0 key open
dhclient wlan0 

modify to suit your environment.

---

