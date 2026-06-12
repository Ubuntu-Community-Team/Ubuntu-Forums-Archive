---
title: "Network manager: wiereless device - device not ready"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by Eberk89 on 2009-10-20
I was making some tests with wpa_gui on my hp pavillon dv6000 when Network Manager started to show "device not ready" under "wireless device". I uninstalled Network Manager and installed Wicd: the wireless connection works fine!! I don't really know if wpa_gui caused the problem or if something else made my NM crazy.
But i need Network manager running, since it supports wpa2 connection! (only this evening I discovered that Network manager include wpa_supplicant)
 
Someone can help me?!
I really have to make it run in a really short time!! :(

thank yoy

---

### Post by t0mppa on 2009-10-20
WICD supports WPA2 just as well as Network Manager, since they both use the wpa_supplicant to handle that one. So, if WICD is working for you, what do you need Network Manager for?

---

### Post by Eberk89 on 2009-10-21
It seemed to me that in the wicd I can't set all the parameters I can set in the Network Manager option panel, I'll try.

Dont' know if I can reproduce this wpa_supplicant.conf in Wicd
> ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=wheel
fast_reauth=0
network={
	scan_ssid=1
	ssid="DEI"
	key_mgmt=WPA-EAP
	proto=WPA2
	pairwise=CCMP TKIP
	group=CCMP TKIP
	eap=TTLS
	phase2="auth=PAP"
}

---

### Post by t0mppa on 2009-10-21
You should find the current templates used by WICD from */etc/wicd/encryption/templates/*. If none of them has exactly the details that you require, you can always create one of your own and then add it to the active templates file to get it recognized. [Here]("http://forums.remote-exploit.org/backtrack-4-bugs-fixes/23748-wicd-peap-mschapv2.html")'s an example.

---

### Post by Eberk89 on 2009-10-22
finally: wicd runs, I made my template.
Thank you!

---

