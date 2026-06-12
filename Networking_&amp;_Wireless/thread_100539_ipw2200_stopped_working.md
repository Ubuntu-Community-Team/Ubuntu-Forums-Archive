---
title: "ipw2200 stopped working"
date: 2005-12-07
forum: Networking &amp; Wireless
---

### Post by coldrick on 2005-12-07
Running Breezy with 2.6.12-10-686 on an Inspiron 9300. Until this morning, wifi worked great (Intel Pro/Wireless 2200BG). Then I changed my access point and ISP - but not my ESSID - and it doesn't work any more (Windows machines are fine, as is the alternate Windows boot on this laptop, so hardware must be OK).

dmesg|grep ieee shows:

ieee1394: Initialized config rom entry `ip1394'
ieee80211_crypt: registered algorithm 'NULL'
ieee80211: 802.11 data/management/control stack, 1.0.3
 ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[394fc0001f44b838]

dmesg |grep ipw
 ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Unable to load ucode
ipw2200: Unable to load firmware: 0xFFFFFFC2
ipw2200: failed to register network device
ipw2200: probe of 0000:03:03.0 failed with error -5

In desperation - and because I'd like to start using WPA, I followed [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623) to install the latest formware, driver, etc., tho I left wpasupplicant disabled.

Same symptom, after a few reboots, addition of ipw2200 to /etc/modules, modprobe and modprobe -r, etc. etc. No joy.

Suggestions?

Regards,
David

---

### Post by vampire on 2005-12-11
Hi

I have the same problem here. The card worked for 2 month but now can't connect to the network anymore. if i scan for networks with iwlist scan it says "no scan results" but i am sure that there is one because 2 other pc's are using it.  

last time i had to reinstall breezy to solve that problem. i think that probleme occures always after starting the laptop at a place where no network is available.

i hope you can help us with that problem und sorry for my bad english(i am german)

p.s: i forgot to mention that i have the same network card (Intel Pro/Wireless 2200BG)

---

### Post by coldrick on 2005-12-16
I finally re-installed. :(

---

