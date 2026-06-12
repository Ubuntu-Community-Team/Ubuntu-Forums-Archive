---
title: "ubuntu noob rtl8192ce"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by coonie on 2012-04-20
new to ubuntu and trying to install a driver for my wireless pci card which is a wf-2113 made by netis wireless the cd that came with it has a rtl8192ce file but I can not figure out how to do anything with it. I have searched all over and can not seem to find what I am looking for yet anything would be helpful at this point. figured I would ask as easy as it was to find and fix the usb adapter I used on my laptop there must be something I am over looking.

---

### Post by chili555 on 2012-04-21
Let's do some diagnostics. Please open a terminal and run and post:```
lspci -nn | grep 0280
lsb_release -rc
demsg | grep 8192
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

What is on the CD, specifically, about rtl8192ce?

---

### Post by coonie on 2012-04-23
lspci -nn | grep 0280
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8178] (rev 01)

lsb_release -rc
Release:    10.04
Codename:    lucid

demsg | grep 8192
No command 'demsg' found, did you mean:
 Command 'dmesg' from package 'util-linux' (main)
demsg: command not found

 dmesg | grep 8192
[    8.076404] 8192cu: USB_SPEED_HIGH
[    8.084246] ====> ReadAdapterInfo8192C
[    8.651750] <==== ReadAdapterInfo8192C

I'd like to go ahead and thank you now, because of you helping someone else my usb adapter works now ):P

---

### Post by coonie on 2012-04-23
> What is on the CD, specifically, about rtl8192ce?a windows driver and a folder for linux inside that folder for linux is something I extracted to my desktop---and inside of that are folders for firmware, hal, realtek, rtlib, and a few other things I am assuming waiting to be compiled after I have been searching around the forum

---

### Post by chili555 on 2012-04-23
> my usb adapter works now Glad it's working. Have fun!

---

### Post by coonie on 2012-04-24
the usb adapter is but I still can't get the pci card going I am using the usb as a temporary solution

---

### Post by chili555 on 2012-04-24
Ahh! I see now. What version of Ubuntu are you running? The latest stable version 11.10 includes rtl8192ce and covers your device.```
lsb_release -rc
```> modinfo rtl8192ce
filename:       /lib/modules/3.0.0-17-generic-pae/updates/cw-3.1/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     5600787336CAC53BBBD687B
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="Red"]10EC[/COLOR]d0000[COLOR="Red"]8178[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl8192c-common,mac80211
vermagic:       3.0.0-17-generic-pae SMP mod_unload modversions 686 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)


---

### Post by coonie on 2012-04-25
lsb_release -rc
Release:    10.04
Codename:    lucid
 I'll update to 11.10 and let you know

---

### Post by coonie on 2012-04-25
started working at 11.04 thank you for your help!

---

