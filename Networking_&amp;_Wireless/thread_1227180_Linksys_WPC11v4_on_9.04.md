---
title: "Linksys WPC11v4 on 9.04"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by beausoleil on 2009-07-30
I'm trying to get WPA(TKIP) working on an old P3 laptop - a Sony Vaio PCG-505JL with 384MB RAM.  I've tried two PCMCIA cars -  Linksys WPC11v4 or an AT&T 6700G (Atheros), with the same results: each  initializes, can successfully scan local nets, and can run without encryption, but I'd like for it to connect to my Netgear WGR614v9 wireless router using WPA.

The router's configured to support B and G modes, and WPA-PSK [TKIP] + WPA2-PSK [AES]. My other two laptops (Dells with built-in wifi) are running in WPA2 mode, and they work fine.

I've configured wlan0 in network manager for WPA & WPA2 Personal, and entered the cleartext password, which apparently gets converted automatically to the hex passphrase.  

dmesg reports that "*wlan0: disassociating by local choice (reason=3)*" - how do I know which wpa mode it's trying to use? It appears that NetworkManager doesn't have any debugging capability.

Since I'm configuring this laptop for a non-Linux friend, I'd like to get NetworkManager to work properly, rather than manually configuring wpa_supplicant. Any hints? I know Linux fairly well, but mostly Fedora and almost no wifi under Linux.


Edit: I also tried an AT&T 6700G B/G card (Atheros chipset) and get the same messages, so I think it's just a configuration problem...

---

### Post by beausoleil on 2009-07-30
Bump...

---

