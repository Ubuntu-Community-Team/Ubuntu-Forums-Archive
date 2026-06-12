---
title: "Cross platform network manager: wpa_gui?"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by J05HYYY on 2010-03-11
Hello, I am looking to find a program similar to nm-applet which can run on NetBSD. So far, I have found wpa_supplicant and wpa_gui. Am I on the right tracks? Basically, I want to scan for wireless networks and connect to them. When I start wpa_gui, I get "Could not find status from wpa_supplicant". Any help with this and I would be in wonderland. Ta.

---

### Post by J05HYYY on 2010-03-13
I followed [the information given here]("http://ubuntuforums.org/showthread.php?t=347269") and started wpa_gui. After doing this, I was able to see my AP appear on the "scan" list. When I click connect, after a few split seconds, it appears with "CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys" and then tries connecting again. I think the driver I am using does not work correctly ... I am using wext - Linux wireless extensions (generic). I have an ASUS Eeepc 1000.
 Apparently the madwifi drivers will work with some sort of patch but I can't work it out. My wireless is working with nm-applet, but nm-applet and wicd is not cross platform - they are Linux specific. Any ideas on this would be nice.

---

