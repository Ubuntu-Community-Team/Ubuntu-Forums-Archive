---
title: "Multiple Wireless Profiles w WPA &amp; wo NetworkMangler"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by Quantumstate on 2012-06-28
I am trying to set up a profile for home and a profile for everywhere else, by manually editing the config files.  It appears that with WPA the main way to set up multiple profiles is in wpa_supplicant.conf .
```
	ap_scan=1

# This is our primary (home) network
network={
	# Accesspoint's SSID (cloaked)
	ssid="Hex"
	scan_ssid=1
	# id_str refers to the entry in /etc/network/interfaces
	id_str="home"
	psk="BigBadSecret"
	# Protocol, keymanagement and ciphers. Must match those that the
	# accesspoint uses  (WPA, WPA2)
	proto=WPA2
	# WPA-PSK=Authentication via pre-shared key, WPA-EAP=Enterprise authentication server.
	key_mgmt=WPA-PSK
	# Acceptable ciphers (no assoc)
	# CCMP=AES cipher part of WPA2 standard, TKIP=TKIP cipher part of WPA1 standard.
	pairwise=CCMP
	group=CCMP
	# Give this network the highest priority
	priority=100
}

# It might be useful to define other networks besides our
# primary network. It is possible to create additional entries
# for these into /etc/network/interfaces, if required. Remember
# to give an id_str in here and use that as the interface name
# in /etc/network/interfaces.

network={
	ssid="any"
	scan_ssid=1
	id_str="any"
	key_mgmt=NONE
	priority=50
}
```
And in interfaces:
```
auto wlan0
iface wlan0 inet manual
	# The file which contains roaming information.
	# We are not really concerned about roaming, but
	# this file contains all of our preferred networks
	# to which wpa_supplicant will connect automatically.
	wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf

	# "home" is a keyword which is used in /etc/wpa_supplicant/wpa_supplicant.conf
	#  to tie this entry and a network definition in wpa_supplicant.conf
iface home inet static
	address 192.168.1.1
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.5
	up ip addr add 192.168.11.1/28 brd 192.168.11.255 dev wlan0 label wlan0:1

iface any inet dhcp
```
Well, what to do?  I put the system to sleep at home and wake it up where I know there is a good open access point, and nothing happens.  When it does not find Hex it seems it should then search for any.  When I ifup wlan0=any it tries but can not get a lease.

Any idears?

---

### Post by josephmills on 2012-06-28
have you thought about having a stand alone firewall box do all that for you ?  like pfsense or ipcop they both have settings for "Guest Networks" as long as have enough network pci cards and slots to put into it and also to use. 

I have a p2 with 256 mb ram running on mine with a 9 gig scuzzy hardrive. total cost for Unit $0 USD  (found in the trash) 

Not sure if this can help at all. Might be overkill for what you are trying to do. But that is all I can offer. Good Luck and I am sure that someone will come along and see this. 

Links 
[http://ipcop.org/](http://ipcop.org/)
[http://www.pfsense.org/](http://www.pfsense.org/)

---

### Post by Quantumstate on 2012-06-28
Understand that this is my laptop, which I carry from place to place.  I need to be able to connect at home, -and- elsewhere.

Besides this laptop, I have a fixed HTPC, and backup server at home, and already have very good security. (I'm a CEH/CNDA)

---

### Post by Quantumstate on 2012-06-29
No one knows?  Am I doing New Science?

---

