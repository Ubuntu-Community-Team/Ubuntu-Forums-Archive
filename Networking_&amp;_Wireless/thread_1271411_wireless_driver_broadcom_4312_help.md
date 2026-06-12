---
title: "wireless driver broadcom 4312 help"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by n00bz on 2009-09-20
hi dont know if this has been answered already, if so please provide a link to where it was answered. 

i visited this site for installing driver for you wireless card.   [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware     ]("http://linuxwireless.org/en/users/Drivers/b43#devicefirmware")in my case broadcom 4312. right, i followed the steps and got to the last bit, it the instructions read 

```
sudo ../../fwcutter/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
```Note that you must adjust the FIRMWARE_INSTALL_DIR path to your distribution. The standard place where firmware is installed to is /lib/firmware. However some distributions put firmware in a different place. 
 
 
**problem. i dont know what to put in between those brackets.  i dont know what path it should be. **

is there a command that tells me where it is? how do i find where that place is?

thanks in advance

---

### Post by Ayuthia on 2009-09-20
The definition was in the first line of that code box:
```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
```

Hope that helps.

---

### Post by n00bz on 2009-09-20
=) thank you

---

