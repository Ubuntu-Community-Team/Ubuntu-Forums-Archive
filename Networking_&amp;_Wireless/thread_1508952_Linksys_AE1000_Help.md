---
title: "Linksys AE1000 Help"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by Rey117 on 2010-06-13
I have the Linksys AE100 working on my Ubuntu laptop however the card seems to pick APs but they seem like they have no strength compared to my Intel Wifi card..The USB adapter is supposed to be better but it doesn't seem like it. Any thoughts? Here is a screenshot.

---

### Post by purelinuxuser on 2010-06-13
> **Rey117 said:**
> I have the Linksys AE100 working on my Ubuntu laptop however the card seems to pick APs but they seem like they have no strength compared to my Intel Wifi card..The USB adapter is supposed to be better but it doesn't seem like it. Any thoughts? Here is a screenshot.

It's probably the difference in the drivers.  Each one reports signal qualities on different scales, and they're not always uniform or accurate.  For instance, my Realtek 8172SE scales networks from 1 to 100, whilst my Realtek RT73 USB wireless card scales networks from 1 to 70.

---

### Post by Rey117 on 2010-06-14
You have a Toshiba laptop too...nice and thanx for the input I figured out the prob! Thank you.

---

### Post by alohadiaz on 2010-08-27
Im setting up a desktop for my 5 year old with dual boot xp/ and ubuntu. I really want him to use the Ubuntu but I cant get my Linksys AE1000 usb wifi to work. Do you have the install for this.

---

### Post by techmik67 on 2011-01-17
[FONT=monospace]
[LIST=1]
[*]download ralink rt3572
[*]tar -C ~/Downloads/ -xf ~/Downloads/RT3572_Linux_STA_v2.5.0.0.bz2
[*]cd into the directory
[*]sed -ir -e  's/^HAS_WPA_SUPPLICANT=n/HAS_WPA_SUPPLICANT=y/' -e   's/^HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n/HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y/'   ./os/linux/config.mk
[*]sed -ir -e 's!^#endif // RT2870 //!          {USB_DEVICE(0x13B1,0x002F)}, /* Linksys AE 1000 */\n#endif // RT2870   //!' ./common/rtusb_dev_id.c
[*]sed -ir -e 's/\tusb_buffer_alloc/\tusb_alloc_coherent/' -e 's/\tusb_buffer_free/\tusb_free_coherent/' include/os/rt_linux.h
[*]sudo gedit common/rtusb_dev_id.c
[*]find
[*]{USB_DEVICE(0x1690,0x0744)}, /* 3572 */
[*]{USB_DEVICE(0x5A57,0x0284)}, /* Zinwell 3572 */
[*]{USB_DEVICE(0x167B,0x4001)}, /* 3572 */
[*]and
[*]add {USB_DEVICE(0x13B1,0x002F)}, /* Linksys AE1000 v1 */
[/LIST]
  14.    save and exit

[LIST=1]
[*]sudo make
[*]sudo make install
[*]sudo su -c "echo -e 'alias ra0 rt3572sta\nblacklist rt2800usb' > /etc/modprobe.d/rt3572sta.conf"
[*]You can add other blacklist modules, here's the list from the Ubuntu page:
[*]rt2870sta, rt2800usb, rt2860sta,  rt2x00usb, rt2x00lib, rt2870sta.  Now's a good time to check 'lsmod' and  unload and blacklist any modules  you find. *Also disable any other wifi  adapter. I had an Atheros. I  had to add to the blacklist: ath9k,  ath9k_hw, ath9k_common.
[*]Then run:
[*]sudo modprobe ra0
[/LIST]



line 7-14 i had to add in recently, like, as in the last 2 or 3 days after "apt-get update/upgrade" to get it to work.[/FONT]

---

