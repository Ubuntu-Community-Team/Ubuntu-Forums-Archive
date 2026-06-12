---
title: "My whole house could run Ubuntu if.. (WUSB11)"
date: 2005-01-04
forum: Networking &amp; Wireless
---

### Post by October on 2005-01-04
I could either find out how to get Linksys WUSB11 v2.6 USB wireless NICs to work (without downloading anything) -OR- could find a capable replacement, preferably G speeds.

---

### Post by hardcandy on 2005-01-04
Are they listed in the system info when they are connected?

---

### Post by October on 2005-01-04
Yes, Computer -> System Configuration -> Device Manager seems to show that it has been detected correctly but I can't get it to actually activate as a network device, at least not via any of the GUI's I have tried.

tail -f /var/log/messages:

```

Jan  4 15:16:25 biggun3 kernel: NET: Registered protocol family 17
Jan  4 15:19:51 biggun3 kernel: usb 2-1: USB disconnect, address 2
Jan  4 15:19:57 biggun3 kernel: usb 2-1: new full speed USB device using address 3

```

from lsusb:

```

isokoira@biggun3 ~ $ lsusb
Bus 002 Device 003: ID 077b:2219 Linksys WUSB11 V2.6 802.11b Adapter
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:c00e Logitech, Inc. Optical Mouse
Bus 001 Device 001: ID 0000:0000

```

Both my sons are currently running Win2000 and both have these USB adapters.  If I can get Ubuntu (or any decent distro, for that matter) to work with these then I have two more converts and my entire 6 machine house-hold LAN will be entirely linux powered :D

---

### Post by az on 2005-01-05
I think it is a prism2_usb device and that is pretty complicated to set up with linux-wlan-ng.  You need the linux-wlan-ng package from universe.  The module is already included and hotplug-loaded automatically.  

You can try ndiswrapper.  You will have to blacklist the prism2_usb module from hotplug.  You may also need a more recent version of ndiswrapper.  It is quick and easy to compile from source...

---

### Post by KenLin on 2005-01-13
I have the wusb11 v2.6. It uses the atmel chipset. Unfortunately I can't get it to work in Ubuntu. I asked Magneto about it and he said the only way to do it is to compile a custom kernel, and even then it was a pain in the ass.

However, Suse 9.2 (which is now available via FTP) handles it flawlessly. After install, I plugged in the wusb11 and a dialog popped up saying it had detected the wusb11 and to insert CD1 to install the firmware. I configured it in YAST, rebooted, and it worked. smoooooth. :-D

---

### Post by az on 2005-01-13
It then should work in Ubuntu if you use a later version of ndiswrapper.

---

### Post by KenLin on 2005-01-13
I don't think ndiswrapper works with atmel.

---

### Post by thayne on 2006-10-31
Nevermind :)

---

