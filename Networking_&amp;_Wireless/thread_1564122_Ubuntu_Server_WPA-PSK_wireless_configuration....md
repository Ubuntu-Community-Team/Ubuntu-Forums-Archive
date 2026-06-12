---
title: "Ubuntu Server WPA-PSK wireless configuration..."
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by aSteve on 2010-08-30
I'm sure this is easier than I'm finding it... I've installed Ubuntu Server 10.04, and - later - installed an Atheros 802.11bg card. While I can find lots of information relating to using Network Manager to roam and switch connections as I do... I want to use a wireless connection to my router from my non-mobile server to my nearby non-mobile wireless router.  I want the connection to be up whenever my server is up - and for the connection to be re-established if, for any reason - for example... power cycling the router... the connection is dropped.

I've got as far as having written a wpa_supplicant.conf file which (after a few seconds) connects when I run:

wpa_supplicant -iwlan0 -c/tmp/wpa_supplicant.conf

I want it to start at boot time - and leave me with an interface wlan0 that works just like eth0 does at the moment with a long trailing ethernet cable to my wireless router.  All the Ubuntu information I can find seems out-of-date... I know /etc/network/interfaces is important, but I am unclear what's best to put in there.

I've seen some howtos which do a 'pre-up /etc/init.d/wpasupplicant start' - but I don't have one of those in /etc/init.d/.  I've also seen howtos that put the data from wpa_supplicant.conf directly into the /etc/network/interfaces file...

I'm guessing there's an "approved" way to go about this... I want to avoid writing a flaky hack of my own, if possible.  What steps should I take to go from where I am (i.e. with a working wpa_supplicant test to having a wireless link that works just like my existing Ethernet link... while remaining as standard-Ubuntu-server as I can?

Any hints or pointers to up-to-date documentation would be much appreciated.

Steve

---

### Post by aSteve on 2010-08-30
Found a solution, I think...

[http://blog.blinker.net/2010/06/20/mac-mini-g4-homeserver-with-ubuntu-linux-10-04-wpa2/](http://blog.blinker.net/2010/06/20/mac-mini-g4-homeserver-with-ubuntu-linux-10-04-wpa2/)

Pity this sort of thing isn't part of the standard Ubuntu documentation...  I needed to know about:

wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

I've not tested what happens if the router becomes temporarily unavailable... but, this is a start, at least.

---

