---
title: "Just upgraded from Breezy to Dapper, and wireless has broken"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by OrangeGoblin on 2006-06-27
I upgraded using the update manager, rebooted, and now my wireless adapter (Netgear MA111) no longer appears in Network settings, and iwconfig lists wlan0 as "no wireless extensions". ndiswrapper lists both the driver and hardware present. How can I fix this, and get my wireless up and running again? Cheers.

---

### Post by Dr. Nick on 2006-06-27
Were you using ndiswrapper in breezy?

If you reboot do you still have access to your breezy kernel?

I would try to boot back into the old kernel if possible, It is possible that the new kernel has native drivers for your card that are not functioning and getting in the way of ndiswrapper.

---

### Post by OrangeGoblin on 2006-06-27
I was using ndiswrapper, I tried booting with what I assume was the old kernel - it was the only other option and it had lower numbers :) - and I saw a bunch of error messages mentioning ndiswrapper as it booted - of course it still didn't work when I finally got to the desktop.

---

### Post by Dr. Nick on 2006-06-27
ok then, Get back into a gui with your newest kernel and run **lsmod** from a terminal. this will show you the drivers listed. Their may be a conflicting driver included in the new kernel for your card. 

If the card is usb look at the usbcore line and post what is listed their, or just post the whole output back here. It may a easy fix by just removing the offending driver and going to ndiswrapper.

---

### Post by OrangeGoblin on 2006-06-27
The usbcore lines reads:

usbcore        129668      4 ndiswrapper,prism2_usb,uhci_hcd

Can't really post the whole output as I'm copying it by hand from one PC to the other, but I hope that's all you need. Thanks.

---

### Post by Dr. Nick on 2006-06-27
Thats perfect!!

Your card is very much like mine, I to have the prism2_usb module

Hopefully a simple fix, Try runnig this command
[B]
sudo modprobe -r prism2_usb[/B]

then 
[B]
sudo modprobe -r ndiswrapper[/B]

and finally

[B]sudo modprobe ndiswrapper

[/B]After those 3 commands it shoud  work aslong as ndiswrapper is set up right,
That will have to be run every time you reboot or unplug/replug the card unless you either delete the prism2 file of just blacklist it, I will dig up the blacklist instructions and put them here, they may work. For me I just chose to delete the prism2 file ;-)
----------------------------------------------------------------------------

I think this is how to properly blacklist it

Add 'prism2_usb' in /etc/modprobe.d/blacklist

then go to /etc/modules and add 'ndiswrapper' to make ndiswrapper load on boot.

---

### Post by OrangeGoblin on 2006-06-27
Brilliant, worked first time. Thanks a lot!

---

### Post by Dr. Nick on 2006-06-27
Glad you got it to work, The prism2_usb driver will work, it just takes a bit more to setup and doesnt seem as stable for me so I stopped using it aswell. I hope they get it more "user friendly" soon so we can have wireless from the first boot without issue.

---

