---
title: "Recommendations: Wireless devices, preferrably..."
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by Stealth on 2006-06-26
I've been looking through the wiki, and I wish it was more updated and easier to search, and not finding what I was really looking for, I thought I'd might as well ask here:

I'd like to buy a wireless adapter (USB is preffered for portablity, but I'd accept PCI cards too) for one of my desktops. It should work fairly easy in Ubuntu, even if some configuration is needed. It would be optimal if it supported WPA**2**, and at the very *least* WPA. Also, I have a router capable of 108Mbps (a DGL-4300) so if it can do that speed it would be cool. As you can see that would seem like some very non-Linux friendly device, so I'm asking here to see if anyone has personally had experienced with a device somewhat like the one I'm looking for...

:) So far, I've got my eye on the DWL-G132, but I can't tell if supports WPA2, otherwise it seems perfect...

That, or if someone knows how to get a SMCWUSBT-G working, ndis reports driver and hardware present, but I have no interface for it (like wlan0 or ath0) -.-

---

### Post by wieman01 on 2006-07-07
Mate... Linksys' Wusb54g worked fine for me. Check this out:

[http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2]("http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2")

Guides you through WPA2 setup using WPA supplicant v0.4.8 & NDiswrapper.

He

---

### Post by patrickfromspain on 2006-07-07
for the ndiswrapper think... after installing the driver, did you do:

sudo ndiswrapper -m
sudo modprobe ndiswrapper

;)

---

### Post by wieman01 on 2006-07-07
> **patrickfromspain said:**
> for the ndiswrapper think... after installing the driver, did you do:

sudo ndiswrapper -m
sudo modprobe ndiswrapper

;)

Is that a question or a statement? I am afraid I cannot follow you...

I probably did though.

---

