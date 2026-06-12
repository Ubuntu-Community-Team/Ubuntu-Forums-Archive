---
title: "/etc/network/interfaces ? (WiFi WEP)"
date: 2005-01-21
forum: Networking &amp; Wireless
---

### Post by MrTrumpets on 2005-01-21
I have my wireless network working, but it only grabbs an IP address if I have WEP turned off.  I can't figure out how to setup the "interfaces" file to try to send WEP info..

can someone give me an example of an "interfaces" file with a working WEP (possibly using a Linksys card using B)

Thanks in advance!

---

### Post by Totson on 2005-05-09
Hi MrTrumpets,

Had the same issue. Would need to constantly issue the "sudo iwconfig ethx key XXXX && dhclient ethx" command before my ipw2200 would peak up the AP and get an IP @

To have it done automatically, edit the "/etc/network/interface" entry for your wi-fi card and include the options you need. Like :

«
# The primary network interface


iface ethx inet **dhcp**
**wireless-essid XXXXXXXXXXX**
**wireless-key XXXXXXXX**

auto eth1
»

Although I don't use the same card, I guess iwconfig uses the same types of options regardless the card. You would need to use the options and values that do it for your hardware I guess.

Cheers

---

### Post by SAMsan on 2005-06-17
[QUOTE=MrTrumpets]I have my wireless network working, but it only grabbs an IP address if I have WEP turned off.  I can't figure out how to setup the "interfaces" file to try to send WEP info..

can someone give me an example of an "interfaces" file with a working WEP (possibly using a Linksys card using B)

Thanks in advance![/QUOTE]
 here's mine for static IPs :

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	#map eth0
	map ra0

# The primary network interface
auto ra0
iface ra0 inet static
wireless-essid XXXXXXXXXXX
wireless-key XXXXXXXXXXX
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.254

---

### Post by andersi on 2005-10-07
This is what did the trick with my equipment (In early Breezy release):
1. use ifdown/ifup to se what happens
2. don't try to use cleartext passphrases in the /etc/network/internfaces -use hexadecimal passkey instead, like this:

/SNIPP
iface eth1 inet dhcp
wireless-essid NETNAME
wireless-key 5BA323BF25
wireless-channel 11
/SNIPP

(I'm using a iw2200 wireless adapter (Fujitsu Siemens Amilo Pro V8010 (W81/EF6)) and a Netgear 108Mbit-router) ..getting a 54Mbit connection (don't think the Fujitsu can do better)

---

### Post by glenn69 on 2007-06-01
If I setup my /etc/network/interfaces with an SSID and WEP key so that my connection works at home, how do I change it when i go to a public hot spot?

Do I have to overwrite the /etc/network/interfaces data with generic settings, or is there a more convenient method available?

---

### Post by derekge on 2008-04-13
> **glenn69 said:**
> If I setup my /etc/network/interfaces with an SSID and WEP key so that my connection works at home, how do I change it when i go to a public hot spot?
yes, I believe you have to overwrite - if you don't use network-manager.

---

