---
title: "Problems using unbranded Ralink USB wireless stick as AP"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by Rhodri James on 2009-05-08
I've been going round and round in circles on this one (including making the leap from Hardy to Jaunty), and I think I need to give up and ask advice.

I have an unbranded (seriously, the only concession to the manufacturer on the packaging is "Made in China") USB wireless device using the Ralink RT2528L chip:

```
rhodri@ghlenlivid$ lsusb
Bus 002 Device 006: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

I've applied the notional fix to net/mac80211/cfg.c to let it work as an AP:

```
static bool nl80211_type_check(enum nl80211_iftype type)
{
	switch (type) {
	case NL80211_IFTYPE_ADHOC:
	case NL80211_IFTYPE_STATION:
	case NL80211_IFTYPE_MONITOR:
#ifdef CONFIG_MAC80211_MESH
	case NL80211_IFTYPE_MESH_POINT:
#endif
+	case NL80211_IFTYPE_AP:
+	case NL80211_IFTYPE_AP_VLAN:
	case NL80211_IFTYPE_WDS:
		return true;
	default:
		return false;
	}
}
```

I've even applied the fix to hostapd that ignores "Unknown" status returns for Association and Authentication Responses from USB devices.

dmesg still gives me:

```
[16303.296014] usb 2-5: new high speed USB device using ehci_hcd and address 6
[16303.589830] usb 2-5: configuration #1 chosen from 1 choice
[16303.699829] phy6 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[16303.699834] phy6 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
```
...though for reasons I don't understand that doesn't seem to alarm anyone on the threads I've managed to find through Google.

Then I create a trivial hostapd config file:
```
rhodri@ghlenlivid$ cat ./hostapd-minimal.conf 
interface=wlan1
driver=nl80211
ssid=test
```

...and try it out:
```
rhodri@ghlenlivid$ sudo ./hostapd ./hostapd-minimal.conf 
Configuration file: ./hostapd-minimal.conf
Failed to set interface wlan1 to master mode.
nl80211 driver initialization failed.
ELOOP: remaining socket: sock=5 eloop_data=0x848b848 user_data=(nil) handler=0x807b930
```

What the heck am I doing wrong?  I'm a newbie when it comes to Linux innards, so you may have to explain things in small words :)

---

### Post by Rhodri James on 2009-05-12
Interestingly, if I do the same on an Acer notebook running 8.10 and the madwifi drivers, I initially get the same result.  If I "ifconfig down" the ath0 interface and use wlanconfig to destroy and recreate it in AP mode, then hostapd runs fairly happily (though I can't get hostapd_cli to work now).  Of course, wlanconfig isn't an option with the hostap drivers, and iw won't do that...

---

