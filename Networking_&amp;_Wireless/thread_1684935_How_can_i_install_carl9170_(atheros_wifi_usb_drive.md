---
title: "How can i install carl9170 (atheros wifi usb driver) on ubuntu?"
date: 2011-02-09
forum: Networking &amp; Wireless
---

### Post by Zyprexa on 2011-02-09
I'm pretty new to the inner workings of linux, so i'm wondering if anyone can tell me how i can replace *ar9170usb* driver with the *carl9170* driver in ubuntu?

The reason i want to do that is that i think it might solve my problems with an unstable and slow Zyxel NWD-271N usb adapter.

---

### Post by dustyboner on 2011-02-14
don't use it. I installed it and it doesn't work as good as the ar9170usb driver. The signal i got with the carl9170 driver was about 10 dBm less than with the ar9170 driver.  Also with the adapter in monitor mode, i couldn't inject because the channel was stuck at -1.


[IMG]http://i479.photobucket.com/albums/rr157/MogoBucketz/lolroflcraflolt.gif[/IMG]

---

### Post by Elludium_Q-36 on 2012-02-09
Is that still the case?

I just got a WNDA3100 v1 with the Atheros ar9170 chip, USB ID 0846:9010 Netgear, Inc. ( USB VENDOR 0x0846 USB PRODUCT 0x9010 ).

I need help installing a linux driver or finding a workable windows .inf file for ndisgtk.  I do plan on doing some work with aircrack-ng, with a gui and that's why I found a v1 with the Atheros Chipset.

I have a couple of links:
[http://wireless.kernel.org/en/users/Drivers/ar9170]("http://www.linuxwireless.org/en/users/Drivers/carl9170")
[http://www.linuxwireless.org/en/users/Drivers/carl9170]("http://www.linuxwireless.org/en/users/Drivers/carl9170")

I'm running Ubuntu 8.04.4 kernel 2.6.24?  

Any helpful advice would be appreciated.

---

