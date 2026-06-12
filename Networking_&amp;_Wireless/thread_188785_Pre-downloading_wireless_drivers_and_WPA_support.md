---
title: "Pre-downloading wireless drivers and WPA support"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by Mr_Cynical on 2006-06-04
I am thinking of switching my dual-boot from Suse to Ubuntu (mainly because Suse refuses to recognise my wireless card even though it is supported). Since Wifi is my only means of internet access, I want to have all I'll need to setup wifi before I install Ubuntu.

Do the following packages come with the Ubuntu installer, and if not can I download them (as .tar.gz or whatever) in Windows beforehand and install them from disc in Ubuntu? (I have a USB key to temporarily store them on)

[LIST]
[*]Atheros drivers (madwifi, since I don't have a .inf driver to use with ndiswrapper) **EDIT:** I am fairly sure that these ARE part of the standard set because the Ubuntu 5.10 LiveCD detected the card as 'ath0' no problem!
[*]wpa-supplicant
[/LIST]

---

### Post by DarthMandeep on 2006-06-04
I know that wpa-supplicant comes with the normal Dapper CD. I'm fairly sure the atheros drivers come with it as well. Have you tried setting up your wireless in the live CD? That seems like the easist way to test support.

---

### Post by Mr_Cynical on 2006-06-04
I'll try the Dapper LiveCD then - I wasn't aware that it came with wpa-supplicant, but I think the Atheros drivers probably will be on it (they were on the previous one anyway)

---

### Post by Mr_Cynical on 2006-06-04
Well, it certainly looks good. Ubuntu recognised my wireless card (even to the point of auto-discovering my wifi network) and it does include wpa_supplicant (I didn't try configuring it because it involves saving files to disc, which on a LiveCD is obviously a problem. I'll do the switch tomorrow (I'm in the UK) - I'm on holiday anyway so I've got plenty of time.

---

### Post by jml on 2006-06-05
Mr_Cynical, its also been my experience that Ateros based wireless cards are recognized by Ubuntu.  If wpa_supplicant is not included on the install cd, I am pretty sure its is available in the Universe repository.  Just for the record, wpa_supplicant is still not officially supported in Ubuntu.  I was never able to get it to work in 5.10.  That's why I resorted to using Mandriva 2006 on my work laptop.  I have not yet had the time to play with wpa_supplicant in 6.06 yet to see if it would work.  Good luck.

Joe

---

