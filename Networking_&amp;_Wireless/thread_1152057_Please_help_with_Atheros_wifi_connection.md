---
title: "Please help with Atheros wifi connection"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by r_avital on 2009-05-07
Folks, I've done a ton of research on my own on this problem, and lots of troubleshooting, with some progress, but still stuck.

Laptop is MSI GX710 with Atheros AR242x 802.11abg Wireless PCI adapter built in.  

Access Point is Netgear WG102 connected (wired) to Netgear Router FVS318.  Any Windows/Mac machine with a working wifi adapter connects to it successfully.

The laptop came preloaded with Windows Vista, and connected successfully with the AP.

I removed Vista and installed Ubuntu 8.10.  Wired connection works perfectly well.  WIFI connection fails.

Based on recommendations in official Ubuntu wireless troubleshooting guide, I installed ndiswrapper, downloaded the windows driver, and installed them via the  utility provided by ndiswrapper (System->Administration>Windows Wireless Drivers).  This tool reports "Hardware present: Yes"

lsmod shows a long list of modules, not sure what I should look for, but it doesn't list anything that looks lik wlan or wifi (it does list ndiswrapper though).

sudo lshw -C network shows that the wifi is "UNCLAIMED" which according to ubuntu means there is no driver loaded.  That conflicts with the above.

Please, any help would be appreciated.  I don't want to resort to buying a USB wifi adapter when there already is one built in.

Thanks in advance

---

