---
title: "Manual wlan configuration (dhcp/no encryption)"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by marko-p on 2010-01-17
Hi,
I cannot properly configure my wlan using "manual mode" (with Network Manager GUI everything works just fine, but just to please the interest)

I use: dhcp, no encryption, broadcasted ssid

I tried theese /etc/network/interfaces combinations:

[PHP]auto wlan1
iface wlan1 inet dhcp
wpa-driver wext
wpa-ssid <my_ssid>
wpa-ap-scan 1[/PHP]

Tried every variaton by deleting a row form bottom to top, till:

[PHP]auto wlan1
iface wlan1 inet dhcp[/PHP]

From the beggining prefix "wpa-*" made me suspisous, so after little bit of browsing, i came to this:

[PHP]auto wlan1
iface wlan1 inet dhcp
wireless-essid <my_ssid>[/PHP]

Everytime any change is done, i enter /etc/ini.d/networking restart command, which is followed by this output:

[PHP]--------------------------------------
* Reconfiguring network interfaces...                                                                                       RTNETLINK answers: No such process
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:1a:9f:91:c5:a2
Sending on   LPF/wlan1/00:1a:9f:91:c5:a2
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:1a:9f:91:c5:a2
Sending on   LPF/wlan1/00:1a:9f:91:c5:a2
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
* Reloading /etc/samba/smb.conf smbd only
   ...done.[/PHP]

By the way, i use some other combination at home (static_ip/wpa/ssid broadcast) which works fine:

[PHP]uto wlan1
iface wlan inet static
address 192.168.1.5
gateway 192.168.1.1
netmask 255.255.255.0
wpa-driver wext
wpa-ssid <mano_ssid>
wpa-ap-scan 1
wpa-proto RSN
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <my_passkey>[/PHP]

So, maybe any suggestions how to configure dhcp without encryption?

---

### Post by marko-p on 2010-01-18
Is it so hard, or is it so easy?
Maybe my problem is not explained very clearly? :(

---

