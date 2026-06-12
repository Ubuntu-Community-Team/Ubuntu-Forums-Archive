---
title: "Wpa"
date: 2005-12-12
forum: Networking &amp; Wireless
---

### Post by doboy007 on 2005-12-12
This is probably not the right place to ask this but is there any way to set up a wireless router to use both WEP (for devices that can't do WPA ie Nintendo DS or PocketPC) and WPA for secure ubuntu goodness?

Probably not?

---

### Post by WildTangent on 2005-12-12
From my rather limited knowledge of wireless networking, I don't believe this is possible unfortunately. If I'm wrong, someone please correct me :)

-Wild

---

### Post by firecat53 on 2005-12-12
The newest Madwifi drivers for Atheros cards are capable of creating multiple virtual access points. That about taps out my knowledge, but it's someplace to look!  :)

Scott

---

### Post by jml on 2005-12-12
The limiting factor is actually the access point itself.  Most modern access points can be set up to use either WEP or WPA but not both at the same time.  If you don't need simultaneous access to the device, simply change the encryption by logging into the set up utility and converting from WEP to WPA.  This won't work if you do not have administrative acces to the access point, or if you need simultaneous access with both systems.

Another idea that I have never actually tried but have read about is to utilize two separate access points.  For example, you can set up two Linksys access points/routers.  One connected to the DSL or Cable modem.  Connect your computers running WPA to this one.  A second Access Point/Router can be set up as a bridge.  Set this one up to run WEP encryption, this access point can then be connected via a CAT5 (ethernet) cable to the other router.  This should accomplish what you want.  I believe the instructions to do this is included in the hardwares documentation.

---

