---
title: "WPA2 authentication fails with rtl8191se in 11.10 (oneiric)"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by ScottMinster on 2011-10-15
I just completed the upgrade to Oneiric (11.10) and I've found that my wireless can no longer connect to my WPA2 secured network.  It thinks for a while, then asks for the password.  This used to work in previous Ubuntu installations (11.04 and 10.10).  I was able to connect to an unsecured connection I had (for some old hardware and I never took it offline).

I'm pretty sure it's using the rtl8192se kernel module.  lspci -v shows the following:

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
	Subsystem: AzureWave Device 1107
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at d800 [size=256]
	Memory at fbefc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: rtl8192se
	Kernel modules: rtl8192se


The syslog has some messages about "Trying to authenticate with XX:XX:XX:XX:XX:XX (SSID='XXXXXXXX' freq=2437 MHz)" (mac address and ssid "X"'d out) and "wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 1/3)" followed by try 2/3 and try 3/3 and finally a timeout after about half a second.

Any ideas what's wrong?  This seems to be some sort of authentication problem, but I'm pretty sure I have the password right (it would have tried what worked before the upgrade, and I've verified it's right in later attempts).

---

### Post by Hrairoo on 2011-10-16
the exact same problem with RT3060/RT2860

EDIT: As it turns out it works in WPA2-PSK but only with TKIP encryption.

---

### Post by ScottMinster on 2011-10-16
Well, it may be that this wasn't a problem with Ubuntu at all.  I don't know.  I noticed that another machine (running Maverick) kept getting disconnected from the wireless access point.  It could usually reconnect on it's own, but sometimes it wanted me to re-enter the password.  Using the existing password which was already in the dialog, it reconnected just fine.

I thought maybe the Oneiric laptop might be causing interference.  But on a whim, I rebooted the WAP.  That made the connection problems go away for the other machine.  After a while, I decided to try connecting again with the Oneiric laptop, and it worked.

I guess the problem must have been in the WAP?  Which is weird, because the problem only started after I upgraded to Oneiric.  It's possible it was a coincidence.  Or maybe the upgrade caused some weird traffic that confused the WAP until it was rebooted.

Anyway, at least for now, it seems that I can connect with Oneiric like I could before, so this is tentatively solved.

---

### Post by tonymaro on 2011-10-18
Had the same issue on my daughter's laptop.  Changing from wpa personal to enterprise and back immediately fixed it.

---

