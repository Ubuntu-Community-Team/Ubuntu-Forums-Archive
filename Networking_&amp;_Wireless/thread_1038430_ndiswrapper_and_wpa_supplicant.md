---
title: "ndiswrapper and wpa_supplicant"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by ngolian on 2009-01-12
I just installed Intrepid on my sister's PC which has a TI wireless card. The acx driver doesn't support WPA so I installed ndiswrapper, but wpa_supplicant doesn't seem to be cooperating with it very well. The annoying thing is when I installed ndiswrapper in the LiveCD environment it worked first time so I thought I could safely go ahead and replace Windows.

Having uninstalled NetworkManager the wifi sometimes works if I start wpa_supplicant manually in the foreground, but any attempt to start wpa automatically in /etc/network/interfaces causes negotiation to fail. Error messages "ioctl[SIOCSIWPMKSA]: Operation not supported" (or it might be "Invalid argument") appear on starting wpa_supplicant, even on the occasions when it does work I think.

I also noticed that if I try to get wpa_supplicant to use its ndiswrapper driver (-D ndiswrapper) it says it isn't supported and falls back to wext. Maybe that's the problem? I'm back at home on a Debian system at the moment so I checked the Debian source package rather than Ubuntu's, but there doesn't seem to be any mechanism in there that would disable certain drivers.

Any ideas? I suppose I'll have to use WEP and make sure the router only accepts certain MACs.

---

### Post by kevdog on 2009-01-14
Most of the drivers nowadays are simply referred to as wext, and not like madwifi, ndiswrapper as they were in previous versions.  If you need specific drivers to be built into wpa_supplicant then you need to compile from source and specifically activate these drivers.  To see what drivers are currently supported by your version of wpa_supplicant:

wpa_supplicant -D

It will list it under the section drivers:

These are the only valid driver options you can use when calling wpa_supplicant.

---

