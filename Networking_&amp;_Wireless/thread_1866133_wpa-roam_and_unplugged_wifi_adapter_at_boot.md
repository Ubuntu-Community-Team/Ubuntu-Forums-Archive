---
title: "wpa-roam and unplugged wifi adapter at boot"
date: 2011-10-21
forum: Networking &amp; Wireless
---

### Post by beldenfox on 2011-10-21
I'm having trouble getting wpa_supplicant's roaming mode to work correctly if my USB wifi adapter isn't plugged in at boot. I'm on a headless server using Ubuntu 11.10 without wicd or network manager.

I'm configuring the wireless interface in /etc/network/interfaces like so:

auto wlan0
iface wlan0 inet manual 
wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
iface default inet dhcp

The contents of wpa_supplicant.conf are boring:

ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
network={
        ssid="Blah"
        psk="Blah"
        id_str="default"
}

Everything works well if the wireless adapter is plugged in at boot. wlan0 is configured correctly and the network works fine. If I unplug the adapter wlan0 goes away; if I plug it back in wlan0 comes back. I can see the wpa_supplicant and wpa_cli daemons coming and going as expected. All is well.

However none if this works if the USB adapter isn't plugged in at boot time. From the log files I gather that the wpa_supplicant daemon is launched but bails since wlan0 isn't available. When I later plug in the wifi adapter the wlan0 interface is not brought up since there are no daemons monitoring it.

Relevant syslog messages:
wpa_supplicant[501]: Could not read interface wlan0 flags: No such device
wpa_supplicant[501]: Failed to initialize driver interface

Is this the way wpa-roam is supposed to work? From what I can gather it is designed to ifup the interface when the adapter is plugged in and ifdown the interface when the adapter is removed. It seems reasonable that if the adapter is not plugged in at boot time wpa-roam should enter the "removed" state e.g. it should launch a daemon to monitor the interface and wait for the adapter to be plugged in. But it does not, at least on my system.

Is this a bug in the way wpa-roam works (in which case I will file a report)? Is there something strange going on on my system? Or is this by design? Anyone know?

---

