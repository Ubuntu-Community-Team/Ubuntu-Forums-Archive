---
title: "DWl-G520 help, madwifi trouble"
date: 2005-02-22
forum: Networking &amp; Wireless
---

### Post by brasilman02 on 2005-02-22
I'm a newbie trying to make the jump, but have encountered difficulty getting my card to work.  Ubuntu did not detect my card on installation, even though I checked and the chipset is Atheros based.

Gnome does not give any card option on it GUI network configuration tool.

When I type iwconfig it prints

lo       no wireless extensions

sit0    no wireless extensions


when I type dmesg I think the problem lies here it prints (on two of the lines)

ath_pci: no version for "ieee80211_ioch_siwrite":found kernal tainted
ath_pci: 0.9.4.0 (experimental)
ath%d: unable to attach hardware HAL status 13

I also tried ndiswrapper with the driver from the cd.  It recognized wlan0 but said 
Net3ab.sys is serialized---this might not work

Well it did'nt.

Is it time to just blow this sucker to smithers? :twisted: 

Any help appreciated.

Interesting note, the gui device manager recognizes it as an atheros chipset wireless device...???....???,,

---

