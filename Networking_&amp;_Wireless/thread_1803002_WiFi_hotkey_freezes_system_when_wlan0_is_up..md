---
title: "WiFi hotkey freezes system when wlan0 is up."
date: 2011-07-12
forum: Networking &amp; Wireless
---

### Post by Dean_Kreger on 2011-07-12
Hi all!  I've been doing some poking around, and I've seen some problems along these lines with other laptops, but I haven't been able to find any for my system... I'm running an [HP Envy15 1270ca]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02246343&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=ca&site=null&key=null&product=4221246") under Ubuntu Server 11.04 (2.6.38-8-server).

**[SIZE=2]DETAILS[/SIZE]**

[LIST]
[*]If I start the system with no **auto wlan0** entry in my */etc/network/interfaces* the wifi hotkey acts as expected: The system detects a dis/connect of the device, and nothing more happens.
[*]If I then issue **ifup wlan0** and attempt to do the same, it detects the disconnect, but if I do not re-enable the wifi quickly the system locks up completely (with or without X).
[*]Furthermore, if the system locks up from disabling the wifi, it will freeze during boot until I re-enable wifi with the hotkey.  But, if the wifi is disabled when **wlan0** is down, then it will boot just fine.
[/LIST]
**[SIZE=2]CONFIGURATION[/SIZE]**

[LIST]
[*]I'm configuring my wifi adapter by hand with *wpa_supplicant*, [configuration can be viewed here]("http://sprunge.us/OVNR").  It's brought up by */etc/network/interfaces* at boot, [as can be seen here]("http://sprunge.us/IZDd").
[*]Could the inclusion of "allow-hotplug" be incorrect?
[/LIST]
**[SIZE=2]OTHER INFORMATION[/SIZE]**[INDENT]I'm not really sure what I need to include for extra info, so I'll just do a few that may be helpful...
[/INDENT]
[LIST]
[*][lshw]("http://sprunge.us/VQCA")
[*][lsmod]("http://sprunge.us/PQER") (brcm80211)
[*][lspci]("http://sprunge.us/JPAI")
[/LIST]

This isn't really a serious problem, and it's currently the only thing I have not got working the way I would like on this laptop.  The unfortunate part is the hotkey's location: between F12 and PRTSCR, two keys I happen to use frequently.  I have only hit it twice accidentally, and the second time I was able it re-enable it before the system locked up.

As a final thought, I'm wondering if I could create an event listener for the USB disconnect and have it bring down wlan0 before a lockup...  Would the hotkey need to be enabled for wlan0 to be brought down?


--
Justin

[P.S.: An action shot of the system!]("http://i.imgur.com/Rg2kg.png")

---

### Post by Dean_Kreger on 2011-07-14
Bump... Anyone?

---

