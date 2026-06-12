---
title: "Wireless not working at startup"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by Tobbz on 2006-06-12
Hi All.

Im running Dapper, and i am having problems gettting my Asus WL-167 USB adaptor to connect to my Asus router on start.

I have to manually run this script to get it to work:
```

#! /bin/sh
sudo ifconfig rausb0 down
sudo ifconfig rausb0 up
sleep 2
sudo iwpriv rausb0 auth 3
sudo iwpriv rausb0 enc 3
sudo iwconfig rausb0 ap *AP mac addr here*
sudo iwconfig rausb0 essid *network SSID*
sudo iwpriv rausb0 wpapsk *my key here*
sudo ifconfig rausb0 up
sleep 2
sudo dhclient rausb0

```

This will get my wireless up and running.
But i would like it to connect automatically.
How would i go about doing that?

Here is my /etc/network/interfaces:
```


auto rausb0
iface rausb0 inet dhcp
        pre-up iwpriv rausb0 auth 3
        pre-up iwpriv rausb0 enc 3
	pre-up iwpriv rausb0 wpapsk *my key here*
	pre-up iwconfig rausb0 essid *network SSID*
	pre-up iwconfig rausb0 ap *AP Mac addr*
	pre-up iwconfig rausb0 channel 1
	pre-up iwconfig rausb0 mode Managed
	pre-up iwconfig rausb0 power off

```

---

Another thing.. WHEN i get my connection up and running, it dies after 2mins of inactivity. And i must run my script to get it connected again.
I did a tcpdump on rausb0, and this is the outcome:
```

11:41:36.913193 IP www.google.dk.www > 192.168.1.2.51226: P 1431:1852(421) ack 502 win 6432
11:41:36.913219 IP 192.168.1.2.51226 > www.google.dk.www: . ack 1 win 5840
11:41:36.920323 IP www.google.dk.www > 192.168.1.2.51226: . 1:1431(1430) ack 502 win 6432
11:41:36.920336 IP 192.168.1.2.51226 > www.google.dk.www: . ack 1852 win 8580
11:41:39.189688 arp who-has 192.168.1.2 tell my.router
11:41:39.189709 arp reply 192.168.1.2 is-at 00:13:d4:2f:e2:10 (oui Unknown)
11:43:51.209855 IP 192.168.1.2.32770 > my.router.domain:  4194+ AAAA? www.ubuntuforums.org. (38)
11:43:56.208711 arp who-has my.router tell 192.168.1.2
11:43:56.209726 IP 192.168.1.2.32770 > my.router.domain:  4194+ AAAA? www.ubuntuforums.org. (38)
11:43:57.208558 arp who-has my.router tell 192.168.1.2
11:43:58.208407 arp who-has my.router tell 192.168.1.2
11:44:01.210953 arp who-has my.router tell 192.168.1.2
11:44:02.210801 arp who-has my.router tell 192.168.1.2
11:44:03.210648 arp who-has my.router tell 192.168.1.2
11:44:06.211192 arp who-has my.router tell 192.168.1.2
11:44:07.211041 arp who-has my.router tell 192.168.1.2
11:44:08.210889 arp who-has my.router tell 192.168.1.2
11:44:11.211433 arp who-has my.router tell 192.168.1.2
11:44:12.211281 arp who-has my.router tell 192.168.1.2
11:44:13.211128 arp who-has my.router tell 192.168.1.2
11:44:16.211671 arp who-has my.router tell 192.168.1.2
... this keeps on and on and on, and then it dies..

```

How do i configure my.router ? it's 192.168.1.1

Any pointers, suggestions, links would really be appreciated.



Best Regards, Tobbz

---

### Post by BitTorrentBuddha on 2006-06-12
Well, I don't know how to help you with the long term solution. However, you can save the script, make it executable, and set it to run at start-up, start-up programs can be found, added, and removed by looking in System -> Preferences -> Sessions and selecting the "Start-Up Programs" tab.

---

### Post by Tobbz on 2006-06-12
Thanks a lot for your reply.
Yes. that would been a temp. solution. :)
How do i go about making the script executable?

---

### Post by v3n0m on 2006-06-12
chmod +x
I guess :)

about your other problem (the dying connection); could it be that some powersaving occurs on your wlan card?

I believe you can set that up via iwconfig,
if you can't find it, try 
man iwconfig, or info iwconfig.

hope this helps :)

---

### Post by Tobbz on 2006-06-12
v3n0m, thanks i'll look into that.

I have added this to my interfaces;
pre-up iwconfig rausb0 power off
That should, AFAIK, keep it from being turned off.

---

