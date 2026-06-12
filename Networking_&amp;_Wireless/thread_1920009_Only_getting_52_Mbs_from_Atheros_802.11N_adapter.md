---
title: "Only getting 52 Mb/s from Atheros 802.11N adapter"
date: 2012-02-03
forum: Networking &amp; Wireless
---

### Post by bakegoodz on 2012-02-03
I got a new dual band 802.11N router to speed up file access in my home. (Linksys e3000 with DD-WRT is awesome BTW) I have 2 laptops that connect 5 ghz at 150 Mb/s or more. My 5 year old Macbook running Lucid is getting 195 Mb/s right now. (AR5008)

    I bought a Ubiquiti SR71-E (Atheros AR928X) adapter for my HTPC that run Lucid (XBMC v10) and I can only get 52 Mb via 5 ghz even though my router is set to do only 802.11N on the 5 ghz AP. It's closer to the AP than my laptops ever are too. It connects via /etc/network/interface because it doesn't have the GUI network manager. The manufacturers specs say it does 802.11n at 5 ghz. The ath9k website says that the adapter has been supported since 2.6.27 kernel. Lucid has a 2.6.32 kernel. I even tried the wireless modules backported from 2.6.38. Is there an option to tell it connect faster or do I maybe need even a newer kernel? Maybe I'll try out the beta of XBMC

---

### Post by bakegoodz on 2012-02-03
The chipset in my HTPC is Atheros AR9280. The chipset in Macbook that connects 4x faster is a Atheros AR5008

---

### Post by bakegoodz on 2012-02-12
Upgraded to Ubuntu 10.10. Still the same problem. My guess is that I'm somehow using an outdated tool or library in my configuration. I have to connect via command line, so I'll share my config files, maybe someone can shed some light on what I'm doing wrong to get 11n speeds.

/etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

/etc/wpa_supplicant.conf (real keys have been censored)
network={
	ssid="livefire"
	#psk="****"
	psk=*************
}

---

### Post by bakegoodz on 2012-02-19
Did lots of testing with different machines and 80211n network adapters. It is definitely a limitation of connecting via command line, or rather by /etc/network/interfaces. I wish I could figure out which script or library has the 54 Mb/s limit. Then I could bug a package maintainer to fix it before Precise comes out.

---

### Post by bakegoodz on 2012-03-01
Woohoo! I was reading about Sensitivity Range (ACK Timing) in wireless and that it only needs to be set to 2x the farthest distance you could be from the access point. So I changed the Sensitivity Range (ACK Timing) in DD-WRT from 2000 to 50 (pretty generous for my house) and the speed went up to 117 Mb/s

---

