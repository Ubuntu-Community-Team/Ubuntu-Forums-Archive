---
title: "Ralink rt3072"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by mitsios on 2010-12-31
I've just bought a GEETEK Hercules USB Wlan adapter, which has the  Ralink rt3072 chipset. The Connection manager can find wireless APs, but  it won't connect to any of those. Also, aircrack-ng does not find any  APs while scanning. What should I do to fix this?

EDIT: After some tinkering and a lot of restarting, I can now connect t  wireless networks, although slowly. However, I still can't use it with  aircrack-ng. Can someone help here?

---

### Post by PatchesTheCaveman on 2010-12-31
There is an updated driver for your wireless card that might exhibit better performance.  To install it, go to Applications > Accessories > Terminal and type the following in the black box that appears and press Enter:
```
sudo apt-get update
```

After that, if you are running Ubuntu 10.04 Lucid Lynx (LTS), type this in and press Enter:
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

If you are running Ubuntu 10.10 Maverick Meerkat, type this in and press Enter:
```
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

Once you have installed the new driver, reboot to let it take effect.

---

### Post by mitsios on 2010-12-31
Unfortunately that didn't have any difference, and I still can't even scan with airodump-ng. Connecting to networks didn't become faster, either.

---

### Post by PatchesTheCaveman on 2010-12-31
The only other thing you can try is to install the official drivers from Ralink.

There are detailed instructions in this thread:  [http://ubuntuforums.org/showthread.php?t=1353044](http://ubuntuforums.org/showthread.php?t=1353044)

---

### Post by mitsios on 2011-01-01
> **PatchesTheCaveman said:**
> The only other thing you can try is to install the official drivers from Ralink.

There are detailed instructions in this thread:  [http://ubuntuforums.org/showthread.php?t=1353044](http://ubuntuforums.org/showthread.php?t=1353044)

I think I did compile some drivers before. Internet is working, but I would like to be able to use the card with aircrack-ng. Is there a solution to this?

---

### Post by PatchesTheCaveman on 2011-01-01
You might try asking on the aircrack-ng forums.  They have more people experienced with that software and can probably help you get it working with your wireless adapter.

[http://forum.aircrack-ng.org/](http://forum.aircrack-ng.org/)

---

### Post by mitsios on 2011-01-05
Anyway, I solved it partially by compiling a kernel and selecting rt2800usb and support for rt3070 from the staging drivers. I can monitor but I still can't inject because I get an error:
"mon0 is on channel -1, but the AP uses channel 6". If someone could help, it would be greatly appreciated.

---

### Post by proxx1850 on 2011-11-08
Maybe I am waking the dead here...


A couple of devices have this problem with the Air..ng suite.
You should try older ubuntu kernels, or just use a backtrack kernel :)
This is dirty fix I know.
At least this way you can verify whether it works or not, and finally burn your fingers compiling your own kernel with.
Or you could just go and use headers.

Dunno if this helps :)

---

