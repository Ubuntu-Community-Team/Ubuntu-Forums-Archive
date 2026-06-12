---
title: "Is karmics /etc/init.d/hostapd broken??"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by WOTHed on 2010-01-21
I'll try to be brief.

```

me@ubuntu:~/home/me$ sudo hostapd -B /etc/hostapd/hostapd.conf
Configuration file: /etc/hostapd/hostapd.conf
Using interface wlan0 with hwaddr 00:14:6c:c3:0d:09 and ssid 'monkey'
me@ubuntu:~/home/me$
```

now if I instead do:
```

me@ubuntu:~/home/me$ sudo /etc/init.d/hostapd start
 * Starting advanced IEEE 802.11 management
   ...done.

```
I doesn't actually work!
As much as  I try the init script way fails and the manual way works.
I looked with an editor at the script and it had /etc/hostapd/hostapd.conf as the config file so I don't know what I'm doing wrong. Or is the distro's (karmic) script bugey?

I have done a distro-upgrade recently and now am  runing 2.6.31-17-generic-pae.

me@ubuntu:~/home/me$ dpkg -s hostapd|grep 'Ver\|Dep'
Version: 1:0.6.9-3
Depends: libc6 (>= 2.4), libnl1 (>= 1.1), libssl0.9.8 (>= 0.9.8f-5), lsb-base (>= 3.0-3)

---

### Post by WOTHed on 2010-01-21
hostapd.conf:

driver=nl80211
interface=wlan0
bridge=br0
hw_mode=g
channel=1
ssid=monkey

---

### Post by WOTHed on 2010-01-30
Ok anyone who wants to know, the answer is this

# sudo vim /etc/default/hostapd

    * Uncomment
          o RUN_DAEMON="yes"
          o DAEMON_CONF="/etc/hostapd/hostapd.conf"

(replace vim with vi, gedit, nano, kwrite, kate or your editor of choice)

Got this from this good hostapd and atheros guide here:
[http://blog.bokhorst.biz/3395/computers-en-internet/asrock-ion-330ht-as-wireless-access-point/](http://blog.bokhorst.biz/3395/computers-en-internet/asrock-ion-330ht-as-wireless-access-point/)

Also if you not on karmic or lucid and/or want to used madwifi instead go here for that part:
[http://blog.robin.smidsrod.no/index.php/2008/08/08/how_to_setup_an_atheros_based_access_poi](http://blog.robin.smidsrod.no/index.php/2008/08/08/how_to_setup_an_atheros_based_access_poi)

---

### Post by WOTHed on 2010-01-30
Ok anyone who wants to know, the answer is this

# sudo vim /etc/default/hostapd

    * Uncomment
          o RUN_DAEMON="yes"
          o DAEMON_CONF="/etc/hostapd/hostapd.conf"

(replace vim with vi, gedit, nano, kwrite, kate or your editor of choice)

Got this from this good hostapd and atheros guide here:
[http://blog.bokhorst.biz/3395/computers-en-internet/asrock-ion-330ht-as-wireless-access-point/](http://blog.bokhorst.biz/3395/computers-en-internet/asrock-ion-330ht-as-wireless-access-point/)

Also if you not on karmic or lucid and/or want to used madwifi instead go here for that part:
[http://blog.robin.smidsrod.no/index.php/2008/08/08/how_to_setup_an_atheros_based_access_poi](http://blog.robin.smidsrod.no/index.php/2008/08/08/how_to_setup_an_atheros_based_access_poi)

---

