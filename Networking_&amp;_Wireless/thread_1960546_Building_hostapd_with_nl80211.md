---
title: "Building hostapd with nl80211"
date: 2012-04-17
forum: Networking &amp; Wireless
---

### Post by Nargren on 2012-04-17
Hello everyone!

I'd like to install hostapd, but with the driver nl80211 included. Now as far as I could research this, I have to compile it for myself and enable the driver since it doesn't come readily installed in Ubuntu 11.10.

I have done the compiling according to a guide found on linuxwireless.org (**[COLOR=Blue][see here]("http://linuxwireless.org/en/users/Documentation/hostapd")[/COLOR]**)
(EDIT...)
Finally I have managed to configure and make it, but after I run
```
make 
```and try to test with e.g.
```
hostapd -dd hostapd-minimal.conf
Configuration file: hostapd-minimal.conf
nl80211: 'nl80211' generic netlink not found
nl80211 driver initialization failed.
```I am sure I did uncomment #CONFIG_DRIVER_NL80211=y
and left it as
CONFIG_DRIVER_NL80211=y

before compiling. This should have allowed nl80211 to be added, no?
Any help would be much appreciated.

Thank you,
Nargren

---

### Post by sakurakig on 2012-07-29
Hello Nargren and all. I'm wondering how you managed to solve this problem. I also want to use hostapd with nl80211 and am exactly at the same step now, and can't make any progress from here.

I'm on Ubuntu 11.10 (which was just upgraded all the way up from lucid). Adding the line
```
driver=nl80211
``` to hostapd.conf resulted in hostapd complaining in that it can't find nl80211: ```
root@WHITE-RAINBOW:/etc/hostapd# hostapd  hostapd.conf
Configuration file: hostapd.conf
nl80211: 'nl80211' generic netlink not found
nl80211 driver initialization failed.
```

I tried to compile hostapd first from ubuntu oneiric sources, 
second from  git://w1.fi/srv/git/hostap.git, 
having installed libnl1-dev, and removing comment from this one line in hostapd/.config: ```
CONFIG_DRIVER_NL80211=y
``` Both time it compiled ok, but result with hostapd.conf was the same. Any help and support how to make hostapd to support master mode for my TL-WN727NV3 will be appreciated.

Something bugs me about if it may be connected with the fact, that there are 2 versions of libnl in Ubuntu 11.10:
```
root@WHITE-RAINBOW:/etc/hostapd# dpkg -l libnl* | grep ii
ii  libnl-dev                                                     1.1-6ubuntu1                                 development library and headers for libnl
ii  libnl1                                                        1.1-6ubuntu1                                 library for dealing with netlink sockets
ii  libnl3                                                        3.0-1.1ubuntu1                               library for dealing with netlink sockets
``` but I couldn't make out if it really mattered and what to do with it.

Update: before anyone reacted - after 1.5 hours of googling I found out that 'modprobe mac80211' would solve my problem (or rather move it to next stage). So it is solved for me now.

---

