---
title: "Bluetooth issue with 64 bit Karmic (9.10) Ubuntu"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by bosbeemer on 2010-02-25
I purchased a new bluetooth dongle that I am having trouble pairing with my bluetooth keyboard. I can see the bluetooth dongle. lsusb gives the following ...

Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

hcitool dev gives the following ...

Devices:
    hci0    00:1F:yx:yx:yx:50

However I'm having trouble pairing my keyboard. After entering the PIN, nothing happens and the dialog returns after a while with and error indicating failed bonding.

I tried it with both blueman and gnome-bluetooth. Similar behavior on both. On some occasions, the bluetooth manager can't even find the keyboard.  

I had another bluetooth adapter with a Broadcom chipset that worked fine.

---

### Post by bosbeemer on 2010-03-04
anyone please. I'm struggling with bluetooth on my 64bit Karmic. It works fine for a while and then goes down randomly. I can't restart bluetoothd. Only a reboot seems to restart the daemon.

thanks in advance.

---

### Post by israel.figueroa on 2010-07-03
Same issue here, I just got two dongles to sync w my phone...

**gnome-bluetooth** and **blueman** show the cell but everytime i try to pair it... gives wrong numbers (diffferent in the laptop and cell), I tried for hours to pair the laptop and cell without luck.

I'm not sure is a dongle issue or a amd64 issue or a lynx issue or even if I'm the problem... but I'm very disappointed of Bluetooth in general.

Is there any known issue about it?
if anyone can give a hand... my specs

```
$uname -a
Linux laptop-lynx 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
```

```
$lsusb
Bus 007 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```

```
$hcitool scan
aa:bb:cc:dd:ee:ff	Celltooth
```

```

blueman_1.21-2ubuntu1_amd64
bluetooth_4.60-0ubuntu8_all
bluez-compat_4.60-0ubuntu8_amd64
bluez-utils_4.60-0ubuntu8_all

```

the cell is a Samsung b3310.

---

### Post by bosbeemer on 2010-07-04
the best thing to do is to get a compatible adapter. I purchased a Targus bluetooth dongle from Staples for $20.

---

