---
title: "ifup calling dhclient before wpa_supplicant is ready"
date: 2011-09-16
forum: Networking &amp; Wireless
---

### Post by bmarty on 2011-09-16
Hi,

I have been recently trying to use ifup and ifdown to configure wireless networks. When I call "ifup wlan0", wpa_supplicant starts up and begins the connection procedure. At the same time however, dhclient is also executed, and attempts to get an IP address, even before wpa_supplicant has initiated a connection. 

Normally, this is fine if the connection is successfully, but if wpa_supplicant cannot connect to the network, dhclient will continuously try to get an IP. Eventually, ifup  will exit with a status of 0, and wpa_supplicant will still continue to run in the background.

Has anyone found a way to make dhclient occur after a success connection is established via wpa_supplicant? If no connection is established, dhclient shouldn't attempt to run.

My only other option I know is to change "dhcp" to "manual" in my interface definition, and call dhcp manually, but I would prefer ifup to handle it if possible.

I have tried setting the interface definition to manual, but it seams that the moment wpa_supplicant is called to connect, ifup believes its ready, not taking into account the time it takes to actually make a connection.

Unfortunately, I am not allowed to upgrade to a newer version of Ubuntu.

Version Information:
Ubuntu: 10.04
wpa_supplicant: 0.6.9
ifup: 0.6.5

My interface definition is:

iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid MYSSID
wpa-key-mgmt WPA-PSK
wpa-proto RSN
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP
wpa-psk "PASSWORD"

Any help would be greatly appreciated!

---

