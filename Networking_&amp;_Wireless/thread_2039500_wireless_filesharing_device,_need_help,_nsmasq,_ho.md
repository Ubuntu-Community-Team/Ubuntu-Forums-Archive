---
title: "wireless filesharing device, need help, nsmasq, hostapd,"
date: 2012-08-09
forum: Networking &amp; Wireless
---

### Post by catgrepuniq on 2012-08-09
I am trying to create a device that appears to be a wireless access point that will server static files to wifi users via web browser.  I need to find a way to intercept and redirect DNS to itself so they will see root dirrectory of lighttpd which is running on the device. 

I can get lighttpd to server files without a problem; they can be seen at [http://127.0.0.1/](http://127.0.0.1/). 

I am also able to get hostapd to make my wireless card appear to be an access point and allow users to connect to it with the following in a hostapd.conf file: 

interface=wlan0
driver=nl80211
ssid=ManyFreeFiles
channel=1

I know what I am trying to do is possible with Ubuntu because I have tested the piratebox livecd and it works on my hardware. [https://github.com/terrorbyte/PirateBoxLive](https://github.com/terrorbyte/PirateBoxLive).

Unfortunately, PirateBox servers files with python, has a lot of scripts, and I do not want to use that. I will be serving 100% static content. 

Does anyone have any suggestions on how to wireless users connected to lighttpd when they connect to my accesspoint?

---

