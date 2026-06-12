---
title: "which version WILL work easily with Dell wireless 11350 mini pci?"
date: 2013-03-24
forum: Networking &amp; Wireless
---

### Post by userqq on 2013-03-24
Hi, I had to reinstall and was having too many issues with the Dell wirelesss 1350 mini PCI aka truemobile 1350, BCM4350 (rev3). with **ver 12.10** on Dell inspiron 9100. I need to use the B43 driver.
Is there any version that will install easily? 
Thank You.
**EDIT: Title should read Dell wireless 1350**

---

### Post by chili555 on 2013-03-24
*IF* your device uses b43, and we don't necessarily know that without additional diagnosis, any and all versions are equally suitable. This driver requires firmware that's pretty easy to install after installation.```
$ modinfo b43
filename:       /lib/modules/3.5.0-26-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
<snip>
```

---

### Post by Bucky Ball on 2013-03-24
You could try plugging in an ethernet cable and do an update then check 'Additional Drivers' for the B43 driver. Enable it. You can also install it manually by installing b43-fwcutter and firmware-b43-installer from the repositories.

And as chilli says, if your card uses the b43 driver ... ;)

---

