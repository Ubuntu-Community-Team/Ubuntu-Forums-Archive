---
title: "D-Link DWL-G122 USB Wireless Adapter"
date: 2006-05-31
forum: Networking &amp; Wireless
---

### Post by obsidianpoet on 2006-05-31
Hello all,

I just got a brand new Dell 5150 desktop with MCE and I am in the process of getting Ubuntu 5.10 installed on it. Eventually I will get MythTV on it as well, but in the mean time I am having some issues surrounding the D-Link DWL-G122 USB Wireless adapter. I have tried the ndiswrapper package with both the windows driver on the CD and the most current on on dlink.com. Ndiswrapper will recognize it, however the lights do not come on on the adapter and there is no wlan option present in the network configuration. Any ideas? Or will I have to break down and get a new wireless adapter/wire a physical drop?

Thanks in advance,

- Obsidian Poet

---

### Post by trorion on 2006-06-02
If you are not using encryption then you should have access by default (rt2570) and it should show up in Aystem->Administration->networking as rausb0.  The drivers for this are supported natively.

You should also be able to use wep.

If you like you can try network-manager-gnome (either through synaptic or sudo apt-get install network-manager-gnome).

WPA is a different story.

---

