---
title: "WG111, ndiswrapper, and WPA"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by tjpren on 2009-09-29
Hello forum, 
Sometimes the saying "if it ain't broke don't fix it" rungs true.

I had my 8.04 with a WG111 wireless USB adaptor connecting to my dlink wireless router using the ndiswrapper, and working well.  I had my SSID hidden, and allowed connection by MAC address.

However, I thought it better to add another level of security, and set up WPA-PSK on the router.

My Kid's windows machines, and my PDA connected OK, once I configured them for the passphrase, but I've met my waterloo with my old Ubuntu workhorse.

I've followed several posts, and modified my /etc/network/interfaces as:

[B]auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid pinkypig
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 92d661bb618071c4e49689e6e722c5a5ee7f887be64286ff860586fdd2a84511[/B]


When I restart, I get the following output:
[B]* Reconfiguring network interfaces...  
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6433
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0f:b5:03:c2:bc
Sending on   LPF/wlan0/00:0f:b5:03:c2:bc
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
ioctl[SIOCSIWPMKSA]: Invalid argument
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0f:b5:03:c2:bc
Sending on   LPF/wlan0/00:0f:b5:03:c2:bc
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/B]

Any ideas - as was mentioned, it was working using the following cofiguration in /etc/network/interfaces :

[B]auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp
wireless-mods managed
wireless-essid pinkypig[/B]

---

### Post by tjpren on 2009-09-29
Hello Forum
_**I could really use your help!!!**_

Since my last post, I've changed the interfaces and supplicant.conf a little:

[B]/etc/network/interfaces

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-mode Managed
wireless-essid pinkypig
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant


/etc/wpa_supplicant.conf

network={
        ssid="pinkypig"
	  scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
	  psk=0e6a43f05bd62909e05ffcb4999dee0905e744d77ce7d7abc6cbf795266cb820
}[/B]

When I do a restart, the USB light flashes but does not connect.

I do sudo /etc/init.d/networking restart, and i get

[B]* Reconfiguring network interfaces...  There is already a pid file /var/run/dhclient.wlan0.pid with pid 5715
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0f:b5:03:c2:bc
Sending on   LPF/wlan0/00:0f:b5:03:c2:bc
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0f:b5:03:c2:bc
Sending on   LPF/wlan0/00:0f:b5:03:c2:bc
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/B]

I don't seem to get an error, but it doesn't connect either.

---

### Post by @ntonius on 2009-10-17
I can only advise you to use karmic 9.10 when it comes out.
I have WG111 v3 and in 9.10 beta works out of the box and there is no need to use ndiswrapper. I have WPA in my router as well and i just typed the passphrase in the field and...that was it. Everything works great

Obviously there was also improvement on the driver because the signal strength is stronger compared to the 9.04 version and i can now access from greater range.

---

