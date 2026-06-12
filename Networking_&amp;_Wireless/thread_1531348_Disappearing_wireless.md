---
title: "Disappearing wireless"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by baguahsing on 2010-07-14
I have 2 wireless adaptors, one is internal, the other is an Asus n-10 usb adaptor.  The internal wireless I can't get to work.  I have an older laptop, a Toshiba Satellite pro 6100.  The internal adaptor is listed as eth1 by ifconfig, iwconfig, and lshw -c network.  So, I bought the usb adaptor which uses the rtl8192su chipset.  After downloading the latest driver from Realtek, I unzipped the file in terminal, did a make, then an insmod 8712u.ko.  Now wlan0 shows up in iwconfig and I can connect using network manager.  When I shutdown or reboot, wlan0 is no longer there only eth1.  How do I get the Asus to start up as wlan0 all the time?  BTW, the internal wireless is can be turned off with a small switch on the side of my laptop.

---

### Post by kerry_s on 2010-07-14
you need to put the " 8712u.ko " in /lib/firmware, so it can be found during boot.

press-> **alt+f2**
type-> **gksudo "nautilus --no-desktop /"**

that should give you a root file manager so you can copy it there.
(you might want to make a launcher for root file manager in the menu, for future needs)

---

### Post by baguahsing on 2010-07-14
Root file manager is not one of my options, only root terminal.  I copied the file to /lib/firmware did a reboot and it still does not auto show up.  Does it matter where in that directory it is placed?

---

### Post by kerry_s on 2010-07-15
> Root file manager is not one of my options, only root terminal.

you make it, just click "new item" fill in the stuff, pick a icon.

>  I copied the file to /lib/firmware did a reboot and it still does not auto show up. Does it matter where in that directory it is placed?

you can try to add the command your using to load it in /etc/rc.local, it's a root file so use the root file manager.

example:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
**insmod /lib/firmware/8712u.ko &**

exit 0
```

---

### Post by baguahsing on 2010-07-15
[QUOTE] you make it, just click "new item" fill in the stuff, pick a icon.
 
Where is this "new item"?  I'm a 2 week old noob, so please be a bit more specific.  The rc-local worked, thanks.

---

### Post by baguahsing on 2010-07-15
I figured it out. Thanks

---

