---
title: "ra0, wlan0 and network-manager"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by HankB on 2011-01-04
I'm working through a problem with no 802.11n on an Eee PC 901 with RaLink RT2860 adapter. It works fine unless I set my AP to "N only." Leaving it as "N and G" allows it to get a G connection (54 Mb/s) but "N only" results in no connection.

I've found instructions for downloading and installing the RaLink driver [http://ubuntuforums.org/showthread.php?t=1592731&page=2](http://ubuntuforums.org/showthread.php?t=1592731&page=2) and have done so. The modified driver module loads but 'iwconfig' lists the interface as 'ra0' instead of 'wlan0'. So named, network-manager and network-manager-applet ignore it.

How can I either get network-manger/-applet to recognize that ra0 is wireless or get the driver to name itself as wlan0? (I'd really rather not manage wireless the old fashioned way.)

thanks,
hank

---

### Post by chili555 on 2011-01-04
Whether it is named ra0 or wlan0 or eth1 or whatever has nothing to do with whether NM will manage the interface. What does matter is if the driver>  is compiled to do so. From the README:> 3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** [COLOR="Red"]Build for being controlled by NetworkManager[/COLOR] or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	   => #>cd wpa_supplicant-x.x
	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
	** Build for being controlled by WpaSupplicant with Ralink Driver
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   => #>cd wpa_supplicant-0.5.7
	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -dAs well, and I doubt this is an issue, NM will not control interfaces listed in /etc/network/interfaces.

---

### Post by HankB on 2011-01-04
Thanks!

I should have read the README. :redface:

And better yet, the driver update fixed the problem with "N only."

best,
hank

---

### Post by chili555 on 2011-01-04
Super! Glad it's working.

---

