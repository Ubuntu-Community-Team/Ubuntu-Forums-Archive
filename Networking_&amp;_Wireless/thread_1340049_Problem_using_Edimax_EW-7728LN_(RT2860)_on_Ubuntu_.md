---
title: "Problem using Edimax EW-7728LN (RT2860) on Ubuntu Server 9.10"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by clev on 2009-11-28
With a clean install of 9.10 64bit server, my wireless card seems to be installed successfully. iwconfig gives:

```
ra0       RT2860 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

"iwlist ra0 scan" works fine also. Therefore, I setup /etc/network/interfaces as follows:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet static
	wireless-essid <networkname>
	address 192.168.1.99
	netmask 255.255.255.0
	gateway 192.168.1.254
```

When I do /etc/init.d/networking restart the following is displayed:

```
 * Reconfiguring network interfaces...
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ra0 ; Network is down.
   ...done.
```

This adds the interface to ifconfig, but does not set up the essid, so I can't access the network. Yet when I manually type:
 ```
iwconfig ra0 essid <networkname>
```

The card connects to the network and I get internet access.

Why does this not work when configured automatically with the interfaces file? Any ideas?

Thanks in advance.

---

### Post by clev on 2009-11-28
After spending some time on this today, I've eventually managed to get it working. The key is to make sure the wireless network is not hidden by your router.

The drivers for RT2860 seem to be included with ubuntu nowadays, but for some reason the card config file is not installed as standard. I downloaded the latest drivers from [www.ralinktech.com](www.ralinktech.com). All I needed was the config file RTA2860.dat. This was copied to /etc/Wireless/RT2860STA/RT2860STA.dat.

Only a couple of modications to the file were required:

```
CountryCode=GB
SSID=<network_name>
```

Reboot and it worked!

Getting WPA up and running was slightly more complicated. Make sure wpa_supplicant is installed (should be with 9.10 server).

Modify RT2860STA.dat with:

```
AuthMode=WPA2
```

Type the following to create wpa_supplicant.conf

```
sudo wpa_passphrase <network_name> <passphrase> >> /etc/wpa_supplicant.conf
```

Edit /etc/wpa_supplicant.conf to see what you have created. I added key_mgmt and proto lines:

```
network={
	ssid="<network_name>"
	proto=WPA2
	key_mgmt=WPA-PSK
	psk=<hex_passphrase>
}
```

Finally, add wpa-conf file to /etc/network/interfaces. Mine now reads:

```
auto ra0
iface ra0 inet static
	wpa-conf /etc/wpa_supplicant.conf
	address 192.168.1.99
	netmask 255.255.255.0
	gateway 192.168.1.254
	dns-nameservers 192.168.1.254
```

---

