---
title: "Unable to Install Wireless card driver (11.04)"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by JoeNixx on 2011-08-11
Good day to everybody, 

I need a little help installing the RaLink driver for my wireless card(D-Link DWA-525) which is known to work well in Ubuntu 11.04.

After compiling the driver, I have tried this, and had no success...

```
jose@jarvis:~$ sudo modprobe rt3562sta
jose@jarvis:~$ dmesg | grep -e rt2 -e rt3
[   10.545043] rt2800pci 0000:04:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.561563] Registered led device: rt2800pci-phy0::radio
[   10.561581] Registered led device: rt2800pci-phy0::assoc
[   10.561601] Registered led device: rt2800pci-phy0::quality
[   10.992274] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[  409.099912] rt3562sta: module license 'unspecified' taints kernel.

```

I can barely understand what's wrong. Could somebody please help me?

Thanks in advance as always.

J

---

### Post by chili555 on 2011-08-11
Let's have a look at:```
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by JoeNixx on 2011-08-11
Thanks to you, Here you go:

```
jose@jarvis:~$ lsmod | grep -e rt2 -e rt3
rt3562sta             874110  0 
rt2800pci              18119  0 
rt2800lib              43824  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              13986  1 rt2800pci
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
```

Glad I can help !

J

---

### Post by chili555 on 2011-08-11
Please do:```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have your report.

---

### Post by JoeNixx on 2011-08-11
Damn, You're Good.

That worked like magic. After the reboot, wireless capabilities were enabled back, and I could properly connect to any wireless network.

Awesome, you don't stop to impress me !

May I know Why did these last command work ?

Fantastic work ! keep it up ! :P

---

### Post by chili555 on 2011-08-11
See post #7 here: [http://ubuntuforums.org/showthread.php?t=1819857&highlight=staging+blacklist](http://ubuntuforums.org/showthread.php?t=1819857&highlight=staging+blacklist)

---

