---
title: "RTL8101e/RTL8012e fix"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by Meigus on 2009-08-07
Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

I discovered a bug and fix for this card.

I installed ubuntu 9.04 from the livecd and the card wouldn't work from startup. Network tools gave something about a "pan0" I think, and there was no internet/connection settings available for the device.

I saw on another site that the card may be a mislabeled 8139 card, and I tried uninstalling the driver and installing a different one, and it didn't work.

After removing the 8139 driver, I restarted to boot into my other OS to check for the card ID. It still said rtl8101e, so I believe that's the card ID.

Much to my surprise, I returned to Ubuntu to find the card configured!

I think there's an error on the installation process from cd, and it requires the current driver to be uninstalled, so the system can correctly configure the driver installation.

To uninstall the driver (if it's installed), I think the commands to use are:

lsmod | egrep "r8|rtl8"
modprobe -r r8101

Upon restart, the card *should* be properly configured.

Note this is the wired card, I don't know if there's a wireless version, or if this will work for that.

---

