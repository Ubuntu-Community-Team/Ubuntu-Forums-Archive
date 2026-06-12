---
title: "Rosewill RNX-EasyN1 ID 148f:3070 Ralink RT2870/RT3070 Disconnects Often"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by kerryhall on 2011-03-31
Hello, I have a Rosewill RNX-EasyN1 USB Wireless N card
lsusb:
Bus 001 Device 072: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter

uname -mr:
2.6.35-22-generic i686

Running Ubuntu 10.10

dmesg:
[http://pastebin.com/m9ag1mqU](http://pastebin.com/m9ag1mqU)

Problem: Getting very low speed (350b to 1 kbps down) I know for sure it is not the network. Also random disconnects.

Using fluxbox rather than metacity, connecting by running nm-applet on startup. Not sure if that matters. Maybe something that gnome starts isn't loading on startup of fluxbox? Running midori as browser, but slow in Links2 and Firefox too.

As a side note: I don't have too much memory on this system and getting more is not an option so I am trying to run on low resources here. Running top I see nm-applet is using 227m virtual, 10m res. Is it acutally using 227 of ram, or what is going on here? Is that just shared libraries? Why would a network manager applet use 227 mb of ram?

Thanks!

---

### Post by kerryhall on 2011-04-07
bump

---

### Post by kerryhall on 2011-04-11
bump

---

### Post by MooPi on 2011-04-11
OKay did you install the driver from Rosewill or Ralink ? Or did the device work plug n play .
Can you give us some info from terminal.
```
lsmod
iwconfig
```

---

### Post by kerryhall on 2011-04-13
Thanks for the reply! The driver was plug and play. Will post outputs from 

lsmod
iwconfig

when I get home tonight. 

Thanks again!

---

### Post by aport on 2011-04-13
I had the same problem... There are issues with the rt2800usb driver. Instead, use the rt2870sta driver.

You can do this by blacklisting the rt2800usb driver:

Add the line
```

blacklist rt2800usb

```
to the file /etc/modprobe.d/blacklist.conf

Now, modprobe the rt2870sta driver. There is a possibility that the driver may not detect your card (it didn't detect mine - Hawking hwun3) so I added this line to /etc/rc.local:
```

echo "0e66 0013" > /sys/bus/usb/drivers/rt2870/new_id

```
This let's the driver see your device without having to modify and recompile the driver - which is a bit of a pain. Of course you would insert "148f 3070" instead of "0e66 0013"

Now just reboot your computer (or rmmod the rt2x000 drivers) and enjoy a fast, stable wireless connection!

---

### Post by Gnobody on 2013-04-09
I'm having the same issue with this same adapter only packet loss is more so the issue, I have a fairly vanilla 64-bit 12.10 installation which no longer contains rt2800sta.
:|  I have tried compiling from source and that didn't work either.


> **aport said:**
> I had the same problem... There are issues with the rt2800usb driver. Instead, use the rt2870sta driver.

You can do this by blacklisting the rt2800usb driver:

Add the line
```

blacklist rt2800usb

```
to the file /etc/modprobe.d/blacklist.conf

Now, modprobe the rt2870sta driver. There is a possibility that the driver may not detect your card (it didn't detect mine - Hawking hwun3) so I added this line to /etc/rc.local:
```

echo "0e66 0013" > /sys/bus/usb/drivers/rt2870/new_id

```
This let's the driver see your device without having to modify and recompile the driver - which is a bit of a pain. Of course you would insert "148f 3070" instead of "0e66 0013"

Now just reboot your computer (or rmmod the rt2x000 drivers) and enjoy a fast, stable wireless connection!

---

### Post by mörgæs on 2013-04-09
The thread is two years old, and the drivers might have changed a lot. Information here is likely to be obsolete.

Closing the thread but you are welcome to open a new one.

---

