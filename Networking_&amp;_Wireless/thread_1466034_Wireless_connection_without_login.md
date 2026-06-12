---
title: "Wireless connection without login"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by brendand on 2010-04-29
Mythbuntu 9.10 (AMD64);

This is meant to be a headless Mythtv backend sitting in a corner recording programs which are uploaded via a wireless connection to some other server for general access.

So wireless connection needs to be automatic (as does wired if wireless fails) because administrative access is via ssh.

I originally had debian lenny on the machine (which of course worked beautifully well) but I couldn't get the tv card and mythtv working.  I did a test install of mythbunutu and got the mythtv side working well enough that I installed it permanently.

I thought I should be able to get the network interfaces out of the clutches of the evil network manager (as I had done) on the debian installation (Ubuntu is debian based, right?..) with the following files:

interfaces:

# The loopback network interface
auto lo
iface lo inet loopback

# The wired network interface
# auto eth1
allow-hotplug eth1
iface eth1 inet dhcp

# The wireless network interface
allow-hotplug wlan1
iface wlan1 inet manual
	wpa-driver wext
	wpa-roam /etc/wpa_supplicant.conf
 
# no id_str, 'default' is used as the fallback mapping target
iface default inet dhcp

# id_str="myid"
iface myid inet dhcp


wpa_supplicant.conf:

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

# WPA-PSK
network={
	id_str="myid"
	ssid="myid"
	proto=WPA2
	key_mgmt=WPA-PSK
	pairwise=CCMP
	psk=mykey
	priority=4
}

However, eth1 does not start automatically on boot (with the cable plugged) or startup when the interface is plugged in (as it did with debian) so obviously the hotplug stuff isn't working as expected.  I can get it going manually with an ifup.

The wireless, however, is way worse.  wpa_cli commands fail to connect to the running instance of wpa_supplicant altogether and I have been unable to get it going using these configuration files.

The wireless card is an atheros based TPLink which connects manually via network manager on the Mythbuntu install.  The other thing to mention is that the version of ath5k that came bottled with debian didn't seem to support wpa of any flavour, so I was using the madwifi drivers from source compiled with m-a.

Please tell me someone has figured out how to make automated wireless network connections work in Ubuntu...

TIA

Brendan

---

### Post by solar george on 2010-04-30
```
#  auto eth1
```
remove the # from that line:
```
auto eth1
```
Should get it working automatically.

> ```
# Connect to access point of ssid 'homezone' with an encryption type of
# WPA-PSK/WPA2-PSK, using the 'wext' driver backend of wpa_supplicant.
# DHCP is used to obtain a network address.
#
iface wlan0 inet dhcp
        wpa-driver wext
        wpa-ssid homezone
        wpa-psk psk

```
altered from [http://svn.debian.org/wsvn/pkg-wpa/wpasupplicant/branches/unstable/debian/README.Debian?op=file&rev=0&sc=0](http://svn.debian.org/wsvn/pkg-wpa/wpasupplicant/branches/unstable/debian/README.Debian?op=file&rev=0&sc=0)

---

### Post by brendand on 2010-05-11
Thanks for that link.  I used it to set up a non-roaming configuration.

However, in the end, I got it working by purging network-manager...

Brendan

---

### Post by iponeverything on 2010-05-11
> **brendand said:**
> Thanks for that link.  I used it to set up a non-roaming configuration.

However, in the end, I got it working by purging network-manager...

Brendan

network-manager is obsessive and sometimes unpredictable in its control of devices.

---

