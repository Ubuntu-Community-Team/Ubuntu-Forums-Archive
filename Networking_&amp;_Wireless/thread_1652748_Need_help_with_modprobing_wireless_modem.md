---
title: "Need help with modprobing wireless modem"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by lonewolf454 on 2010-12-25
I have been trying to figure out how to get my wireless phone/modem to work automatically upon booting ubuntu.  I have it set up to work with a launcher that was the only way I found it to work with hardy.  Now, with newer versions it is auto detected? but only after I modprobe.  I am having to sudo modprobe, and cant figure out how to do it without sudo and password in script.  If I modprobe without sudo, I get:
anthony@Desktop-PC:~$ modprobe usbserial vendor=0x22b8 product=0x2ac4
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-modem, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
FATAL: Error inserting usbserial (/lib/modules/2.6.32-26-generic/kernel/drivers/usb/serial/usbserial.ko): Operation not permitted

but if I add sudo it prompts for password, then will automatically connect.  This is a real nuisance, because I have additional users on this computer that cant connect at all unless I first login and sudo modprobe.  

I tried chmod usbserial.ko to 777 and chown from root to anthony:dip but still same output, not permitted to add usbserial to the file.

---

### Post by sharke on 2010-12-25
Add your sudo modprobe command to /etc/rclocal .
cheers
sharke

---

### Post by lonewolf454 on 2010-12-25
What I really want is a solution not requiring using sudo, so Ubuntu won't prompt for (my) password.

---

### Post by mikewhatever on 2010-12-25
Yeap, /etc/rc.local or /etc/modules. The module should be loaded at boot, obviously, no password or sudo is required.

Running modprobe without sudo would require adding an alias to the sudoers file, but why would you do that.

---

