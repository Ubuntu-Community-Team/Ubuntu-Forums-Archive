---
title: "dell wireless 1395 trouble with ubuntu 9.10"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by syed.rakib.al.hasan on 2010-03-02
i am using a dell vostro 1510 laptop
my wireless card is dell wireless 1395 wLan built-in card
i used ubuntu 8.10 previously and it auto detected my wireless card.......... i had to activate it from  the proprietary devices list in SYSTEM > ADMINISTRATION > HARDWARE DRIVERS
it got activated and it worked fine

now i removed 8.10 and installed ubuntu 9.10 and when i go to SYSTEM > ADMINISTRATION > HARDWARE DRIVERS, it's not even listed in proprietary devices list......... it says "No proprietary drivers are in use on this system" even after keeping the wifi device switched on.

hence i am not able to use wifi from my laptop after installing ubuntu 9.10
i am using ubuntu 9.10 CD which was shipped from canonical upon request.

rakib

---

### Post by bkratz on 2010-03-02
> **syed.rakib.al.hasan said:**
> i am using a dell vostro 1510 laptop
my wireless card is dell wireless 1395 wLan built-in card
i used ubuntu 8.10 previously and it auto detected my wireless card.......... i had to activate it from  the proprietary devices list in SYSTEM > ADMINISTRATION > HARDWARE DRIVERS
it got activated and it worked fine

now i removed 8.10 and installed ubuntu 9.10 and when i go to SYSTEM > ADMINISTRATION > HARDWARE DRIVERS, it's not even listed in proprietary devices list......... it says "No proprietary drivers are in use on this system" even after keeping the wifi device switched on.

hence i am not able to use wifi from my laptop after installing ubuntu 9.10
i am using ubuntu 9.10 CD which was shipped from canonical upon request.

rakib

From what I have found in a few other posts the wireless is most likely a renamed BCM4312 low power (b/g). You can verify this with (in the terminal)

```
lspci
```
(that is LSPCI in lowercase)

If so,  [http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

Shows that it is only supported by b43 with kernel version 2.6.32

14e4:4315
supported 2.6.32 and later
BCM4312
b/g
LP
b43


Do you know your kernel version? If not,
in the terminal enter

```
uname -mr
```
  and see what it says.  We can determine a direction to take once we know the correct model model number and kernel version.

---

### Post by Megaptera on 2010-03-02
I know this simple suggestion refers to Dell Mini, but it worked on my Dell Inspiron 1545 laptop, may be worth a try?

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

