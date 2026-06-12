---
title: "Using a USB Wireless stick instead of my internal wireless adapter"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by TheDelChop on 2010-07-25
Guys,

Title says it all.  I am having some problems with my internal wireless adapter for my laptop.  So, I got my hands on a well known linux compatible ASUS N-13 USB Wireless stick.

However, when I plugin in the USB wireless stick, I can't seem to tell if Linux recognizes it.  

I'm looking for some help getting Linux to recognize that I don't want to use my old internal wireless adapter and I want to use the new USB wireless stick that I bought.

Could anybody help me make this happen?

Thank you,

Joe

---

### Post by Bachstelze on 2010-07-25
See if you can just disable the internal wireless NIC in your BIOS, that would make your life much easier.

---

### Post by TheDelChop on 2010-07-25
I tried to disable it in the BIOS, no luck.  There must be a way to do it in Ubuntu.

---

### Post by flash63 on 2010-07-26
Hello,
a new Udev-Rule can do that.

More Informations about the internal Card and the USB-Stick are required. Connect the Stick, open a Terminal, write the following commands and copy the output:
```

lspci -nnk | grep -i net -A2
lsusb
lsmod
```

---

### Post by Bachstelze on 2010-07-26
An udev rule is a bit overkill, just blacklisting the modules should do the trick.

---

### Post by flash63 on 2010-07-26
That' right, but sometimes the driver is needed to deaktivate the killswitch (mac802.11-Subsystem) at startup. If the killswitch is on, the Stick also don't work. 

In any case, it would be important to know the installed Chipset. Maybe there is only a little Problem with the driver.

---

