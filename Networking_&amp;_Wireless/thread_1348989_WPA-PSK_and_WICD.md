---
title: "WPA-PSK and WICD"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by sgupta1717 on 2009-12-07
Hi.

I can't get my 9.10 Ubuntu to connect to my Netgear MR814v3 using WPA-PSK.  It seems the auth keeps failing.  I use WICD.

I attached wicd.log, wireless-settings.conf, and the file from /var/lib/wicd/configurations/.

You'll want to start at 19:13:25 in wicd.log.  This line is a problem:

2009/12/07 19:14:01 :: wpa_supplicant authentication may have failed.


*-network
description: Wireless interface
physical id: 1
logical name: wlan1
serial: 00:08:a1:b9:a8:25
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+rt2500usb driverversion=1.55+Ralink,08/13/2004, 1.02.01. ip=192.168.0.3 link=yes multicast=yes wireless=IEEE 802.11g


wireless-settings.conf
-------------------------
[00:0F:B5:53:FF:08]
afterscript = None
bssid = 00:0F:B5:53:FF:08
ip = None
dns_domain = None
quality = 100
gateway = None
use_global_dns = 0
strength = -31
encryption = True
bitrates = 1 Mb/s
postdisconnectscript = None
beforescript = None
hidden = False
channel = 7
essid = wpatest
has_profile = False
netmask = None
predisconnectscript = None
enctype = wpa-psk
dns3 = None
dns2 = None
dns1 = None
use_settings_globally = 0
use_static_dns = 0
apsk = mytest17
encryption_method = WPA
mode = Managed
search_domain = None


/var/lib/wicd/configurations/000fb553ff08
---------------
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant
network={
       ssid="wpatest"
       scan_ssid=0
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk="mytest17"
}


Any ideas?  Thanks.

---

