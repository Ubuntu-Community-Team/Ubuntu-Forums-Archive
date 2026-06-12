---
title: "Issues installing wireless network card using ndiswrapper"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by si_pro on 2010-11-21
Hi all!
 
I'm having a tough time installing my wireless network card on Ubuntu. I have been following this how-to [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
 
I have installed ndiswrapper and ndisgtk. I have blacklisted the standard bcm43xx drivers to remove conflicts and managed to install the driver for my card using ndisgtk.
 
Previously, the network connection icon in the tray (top right) had a section for wireless, although it was not working (firmware not present). Since blacklisting the bcm43xx driver there is no section for wireless networking at all.
 
I believe I have done everything up to section 3.6 (configuring the network). The problem is that I do not seem to have the networking options the guide describes (**System** | **Administration** | **Networking**). I have (**System** | **Administration** | **Network tools**) but there is no option to enable roaming or enter the settins it suggests. I cannot see my wireless network from the computer. Oh and I have Ubuntu 10.10.
 
After reading several tutorials I am well and truly stuck!! Any help would be greatly appreciated :)

---

### Post by chili555 on 2010-11-21
Let's do some diagnostics. Please open Applications > Accessories > Terminal and do:```
sudo modprobe ndiswrapper 
ndiswrapper -l
iwconfig
```If 'ndiswrapper -l' says 'alternate driver :ssb' then also run:```
sudo lshw -C netwrk
```We may not be able to blacklist the conflicting driver *ssb* if it's also used by your ethernet card.

Please post the result of these terminal commands.

---

### Post by si_pro on 2010-11-21
Did that and realised that another driver was conflicting and blacklisted that one too.  All works now, woohooo.  Thanks.

---

