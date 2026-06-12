---
title: "WPA and IPW2200 HELP!! Intermittent Connection Only"
date: 2006-01-17
forum: Networking &amp; Wireless
---

### Post by bennettg on 2006-01-17
Hello. A big nOOb here just one step away from say Bye Bye to Bill Gates Forever, but I need help.


I am soooo close. I wiped my hard drive and did a fresh install of kubuntu/ubuntu. I followed luca_linux's instructions in post 1 of this the thread located at [http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

Upon rebooting, I was connected!!!! The speed was much slower than in windows with wpa or in kubuntu with wep, but I was pleased.

However, since that time, I have only been able to connect wirelessly 1 out of 7 times. I wonder if it is something in my /etc/wpa_supplicant.conf file.

To help solve this probelm, I will post a picture of the wireless security settings from my router, and my /etc/wpa_supplicant.conf file. Does it have anything to do with TPIK? My WPA passphrase in ascii and i do not broadcast my ssid.

[IMG]/home/bennettg/Desktop/snapshot1.png[/IMG]

see attached snapshot





Here is my etc/wpa_supplicant.conf:


# Minimal /etc/wpa_supplicant.conf to associate with open
# access points. Please see
# /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
# configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
### Scans/ESSID changes can be done with wpa_cli
network={
ssid=""
key_mgmt=NONE
}

ctrl_interface=/var/run/wpa_supplicant

network={
ssid="acorn"
scan_ssid=1
psk="24334B4A44412423486A736B61"
priority=2
}


If I can just get this to connect reliabily, I will delete windoze from my partitions. Bye Bye M$ and Bill Gates

---

### Post by matthew on 2006-01-17
I've posted a followup to your identical post in [this thread]("http://ubuntuforums.org/showthread.php?p=665827#post665827"). I would recommend for simplicity we stick with just one thread at a time. This is probably a better forum to post the problem in, so I'll PM a moderator and see if they can move that thread here.

---

