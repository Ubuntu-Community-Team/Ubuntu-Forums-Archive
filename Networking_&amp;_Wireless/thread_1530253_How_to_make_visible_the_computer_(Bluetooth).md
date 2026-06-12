---
title: "How to make visible the computer? (Bluetooth)"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by jonah_sao on 2010-07-13
Hi,

I have a Bluetooth dongle and I'd like to make visible my computer, but I don't know how to do that without using any desktop like Gnome, KDE, etc. (I'm trying to do a kind of server, so I don't need/want to install a desktop on it). 

The BT dongle works correctly because I'm able to launch commands like "hcitool scan" to find BT devices around the computer, but for example from my phone I'm not able to find the computer, so I suspect that this happens because the default BT configuration is set as "hide".

¿Does anybody knows what configuration files should I modify to make visible my PC? Or maybe it's not about configuration files, but launching other commands?


I'm using Ubuntu 10.04.

Thanks in advance!

---

### Post by jonah_sao on 2010-07-15
I found the solution more or less here:

[http://wiki.debian.org/BluetoothUser](http://wiki.debian.org/BluetoothUser)

> In order for the pairing to work as described above, your computer's bluetooth interfaces must be discoverable. A bluetooth dongle may start off in hidden mode (bug report here)

To fix this you can run:

# dbus-send --system --dest=org.bluez /org/bluez/hci0 org.bluez.Adapter.SetMode string:discoverable

Or using hciconfig:

# hciconfig hci0 piscan

Then hciconfig should show the flags ISCAN PSCAN, indicating bluetooth is discoverable (i.e. can be scanned). After you finished pairing, it's best to make your computer hidden again: Or using hciconfig:

# hciconfig hci0 noscan

But in my case this wasn't enough. For an unknown reason, the BT dongle that I'm using has a diferent class depending the computer. For example, on a PC with a full Ubuntu 10.04 installation I get this class device:

> hci0:	Type: USB
	BD Address: XX:XX:XX:XX:XX:XX ACL MTU: 1021:8 SCO MTU: 64:1
	**Class: 0x5a0100**
	**Service Classes: Networking, Capturing, Object Transfer, Telephony**
	Device Class: Computer, Uncategorized

But in the computer with a Ubuntu 10.04 installation from debootstrap it has this device class:

> hci0:	Type: USB
	BD Address: XX:XX:XX:XX:XX:XX ACL MTU: 1021:8 SCO MTU: 64:1
	**Class: 0x4a0100**
	**Service Classes: Networking, Capturing, Telephony**
	Device Class: Computer, Uncategorized

Don't know why this happens, but it can be easily corrected with the following command:

```
hciconfig hci0 class 0x5a0100
```


Cheers.

---

### Post by rytec on 2011-08-25
thanks a lot for this extra information.

---

