---
title: "Wireless Trouble on 10.10"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by JadedWolf on 2011-01-01
a

---

### Post by PatchesTheCaveman on 2011-01-01
Hi JadedWolf.  Happy New Year!

Please run these commands and copy/paste the output to a reply to this thread:
```
lspci -v
lsusb
sudo iwconfig
ifconfig -a
```

With that information, we should be able to figure out what's going on.

---

### Post by JadedWolf on 2011-01-01
a

---

### Post by PatchesTheCaveman on 2011-01-01
You can try downloading updated drivers for your wireless card.  To do so, you will need to plug into a wired Ethernet Internet connection.

Once you're hooked up, run these commands:
```
sudo apt-get update
sudo apt-get install linux-backports-modules-wireless-`lsb_release -cs`-generic
```

Please note that the ` character used above is an "accent grave" or "backtick", not an apostrophe/single quotation mark.  You can find to the left of the 1 key and below the Escape key on most US keyboards.

---

### Post by JadedWolf on 2011-01-01
a

---

### Post by PatchesTheCaveman on 2011-01-01
Sorry, I forgot to tell you to reboot afterwards and then try and connect to a wireless network to see if that helped.

If it didn't run this and copy/paste:
```
dmesg | grep -i rt61
```

---

### Post by JadedWolf on 2011-01-01
a

---

### Post by PatchesTheCaveman on 2011-01-01
That's very strange.  You should have gone to the graphical login screen.

Run this command to restart your computer:
```
sudo reboot
```

---

### Post by JadedWolf on 2011-01-01
a

---

### Post by PatchesTheCaveman on 2011-01-01
The command is *sudo re**boot***, not *restart*.

---

