---
title: "Atheros AR242x woes on my ASUS-X59SL laptop"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by kgish on 2009-05-09
Why is it that every time I upgrade to a newer version of the linux kernel my wireless connection stops working? :(

The only way to get around this (it seems) is to reinstall my madwifi-hal-0.10.5.6-r3879-20081204 driver and reboot.

I'd think that by now Ubuntu should support this by now, or am I mistaken?

This is my configuration:

Ubuntu: 9.04
Linux: 2.6.28-12-generic
Laptop: ASUS X59SL-AP275C
Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Does anyone out there happen to have any suggestions?

---

### Post by superprash2003 on 2009-05-09
you could always stick to the old kernel by choosing the old kernel when you boot

---

### Post by kgish on 2009-05-09
> **superprash2003 said:**
> you could always stick to the old kernel by choosing the old kernel when you boot

Not much of an option if I want to keep abreast of the latest and greatest versions.

---

### Post by binbash on 2009-05-09
My card is also using that chipset.First, 2.6.28-12-generic kernel comes with partial upgrade.Default installation of ubuntu DOES support that chipset from my experience.It also works with *.29 kernel out of the box.

You can find the debs here : 

[http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.29.1/](http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.29.1/)

---

