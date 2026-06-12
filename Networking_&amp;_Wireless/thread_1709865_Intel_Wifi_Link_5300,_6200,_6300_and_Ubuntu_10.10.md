---
title: "Intel Wifi Link 5300, 6200, 6300 and Ubuntu 10.10"
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by love &lt;3 on 2011-03-18
This is a solution for those of you who were duped into purchasing engineering samples rebadged as genuine retail units. I take no credit for this, I only have consolidated the already available information, and made it ubuntu specific.

wget [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2)
tar -jxf compat-wireless-2010-10-16.tar.bz2
cd compat-wireless-2010-10-16
gedit drivers/net/wireless/iwlwifi/iwl-eeprom.c
#*** DELETE THREE LINES, 627, 628, 629
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot


Since our engineering sample units are post-production, they contain old eeprom versions that are unsupported by the driver. We remove the function that checks the version so we can use the driver anyway. For reference the lines we delete (627 through 629) are:

    if (eeprom_ver < priv->cfg->eeprom_ver ||
        calib_ver < priv->cfg->eeprom_calib_ver)
        goto err;

---

### Post by Carl.Spackler on 2011-10-02
I just had the misfortune to pick up a couple of 6200 cards from eBay and of course they are ES. :(

I just wanted to update love's information here with the 10/1/2011 version of the compat-wireless driver.

new link: [linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2011-09-27.tar.bz2]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2011-09-27.tar.bz2")

tar -jxf compat-wireless-2011-09-27.tar.bz2
cd compat-wireless-2011-09-27
gedit drivers/net/wireless/iwlwifi/iwl-eeprom.c
#*** DELETE THREE LINES, 233, 234, 235
#*** SAVE FILE

make
sudo make install
sudo make unload
sudo reboot


#*** WE ALSO DO *NOT* NEED THE FOLLOWING LINES REMOVED - THE NEW VERSION OF THIS FILE ALREADY HAS THE CORRECTIONS!!!
#*** gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build

---

