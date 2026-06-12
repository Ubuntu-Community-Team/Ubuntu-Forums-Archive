---
title: "HP nx8220 Enable Bluetooth Radio"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by bradmallan on 2009-10-31
Hi All,

I have an nx8220 without dual boot to Windows. Does anyone know how I can enable the bluetooth radio.

The 'Wireless Networking Button' on the keyboard seems to disbale/enable wireless networking successfully, I just can't get the Bluetooth radio turned on.

Tried this:
brad@ubuntu-hp-laptop:~$ sudo -s
root@ubuntu-hp-laptop:~# hcitool scan
Device is not available: No such device
root@ubuntu-hp-laptop:~#

Also found this archived post:
[http://ubuntuforums.org/archive/index.php/t-189131.html](http://ubuntuforums.org/archive/index.php/t-189131.html)
...it seems to me that Kreso had a dual boot system.

Any help greatly appreciated.

---

### Post by exXplode on 2010-02-19
Just in case this is still a problem for you:

When I press the wireless button on laptop it connects both, the Intel WLAN chip as well as the bluetooth chip. I have no Windows installed on my computer. Maybe you need to activate the bluetooth on your windows installation and leave it on when rebooting! I remember there was a tool from HP to control the Bluetooth module (independently from WLAN) on Windows.

when my wireless stuff is activated (button shines blue) I see the bluetooth device:
```
philipp@lion:~$ hcitool dev
Devices:
	hci0	00:10:C6:F8:05:C6
```

---

