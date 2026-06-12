---
title: "Ubuntu 8.10 &amp; Atheros AR2413 &amp; compat-wireless - wlan not working"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by ELWisty on 2009-03-09
Hi,

I (too) have problems getting wlan working in Ubuntu 8.10. I have Acer Aspire 5040, Ubuntu 8.10 with latest kernel version (dual boot with XP: there wireless works automatically), Atheros AR2413 802.11bg NIC

I followed the instructions of installing compat-wireless on this website:

[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/#comment-956](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/#comment-956)

And those regarding the wpa_supplicant here:

[http://madberry.org/2008/08/wireless-with-wpa_supplicant-easier-then-you-think/](http://madberry.org/2008/08/wireless-with-wpa_supplicant-easier-then-you-think/)

blacklisted conflicting drivers; had ath5k to load at startup; rebooted; tried the wireless button and Fn + F2 no effect. 

Am now in this situation: Network manager has 'Enable Wireless' ticked, and Wireless networks show up in the list of connections but inactive. Otherwise: pastebins at the end of this post. Note: I had tried both ndiswrapper and madwifi before with poorer results.

Any added help would be appreciated as this is quite frustrating.
Thanks a lot.

-iwlist wlan0 scan:

iwlist wlan0 scanning
wlan0     No scan results

-iwconfig:

[http://paste.ubuntu.com/128837/](http://paste.ubuntu.com/128837/)

-lshw -C network: 

[http://paste.ubuntu.com/128836/](http://paste.ubuntu.com/128836/)

-ifconfig:

[http://paste.ubuntu.com/128839/](http://paste.ubuntu.com/128839/)

-dmesg:

[http://paste.ubuntu.com/128842/](http://paste.ubuntu.com/128842/)

---

### Post by ELWisty on 2009-03-09
Some questions I have:

-Can the problem be that the compat-wireless instructions are for a later model of the wireless card?

-in Iwconfig: why does the logical name for the wireless interface show up as wmaster0 rather than wlan0?

-in Ifconfig: does the wlan0:avahi thing cause problems? 

sudo /etc/init.d/networking restart gives:

[http://paste.ubuntu.com/128859/](http://paste.ubuntu.com/128859/)

In System > Administration > Network tools > Devices:

-For Wireless interface (wlan0), 'not available' in Hardware address, multicast, MTU, link speed and state; no interface
-For unknown interface (wmaster0), same as for above
-For Wireless interface (wlan0:avahi), hardware address is shown, multicast enabled, MTU 1500, link speed not available and state active; no interface statistics

---

