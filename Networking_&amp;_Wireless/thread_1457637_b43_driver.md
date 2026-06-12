---
title: "b43 driver"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by Chaos_Spear on 2010-04-18
Need help installing b43 driver to use monitor mode on my card - versions are compatible, I ran 
```
sudo apt-get install b43-fwcutter
```
as told, but instructions end there.  Pressed yes to download and extract firmware.  Do I need to activate this driver somehow?

Info on wireless card:
```
tnt@Artemis:~$ lspci -vnn | grep 14e4
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```

Broadcom STA driver is activated in the hardware drivers manager.

---

### Post by 2hot6ft2 on 2010-04-18
This is for 9.10 but since it still has to do with that driver maybe it will help.
[Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")

LOL, I see you just changed your profile from
Kubuntu Jaunty 9.04
to
Ubuntu 9.10 Karmic Koala
but Kubuntu Jaunty 9.04 is still in your signature unless you're changing that right now.
:lolflag:

---

### Post by bkratz on 2010-04-18
> **Chaos_Spear said:**
> Need help installing b43 driver to use monitor mode on my card - versions are compatible, I ran 
```
sudo apt-get install b43-fwcutter
```
as told, but instructions end there.  Pressed yes to download and extract firmware.  Do I need to activate this driver somehow?

Info on wireless card:
```
tnt@Artemis:~$ lspci -vnn | grep 14e4
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```

Broadcom STA driver is activated in the hardware drivers manager.




The b43 driver is not compatible with any kernels less than 2.6.32 for your particular card, you have to use the STA driver. See the following:

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

---

