---
title: "Swapping between wired and wireless w/ hotplug"
date: 2006-02-03
forum: Networking &amp; Wireless
---

### Post by itmarshall on 2006-02-03
I'm running Breezy on an IBM T41 laptop, with wireless (rt2500 chip) on a PCMCIA card. 

I've successfully got the WPA connection working to my router, and have configured the card to automatically connect when I plug it in, but I have to manually disable the wired ethernet adaptor, eth0 before I can use it. The wired ethernet adaptor is started automatically at boot up.

Currently, I must "sudo ifdown eth0" before the default route gets switched over to my ra0 card. Is there a way that I can get Ubuntu to switch between the devices automatically? When I have the wired connection in, I want to use that, otherwise, I want it to get out of the way. 

I know that "mii-tool eth0" will tell me if I have a physical connection, but how do I tell hotplug to disable the device when it loses the physical connection, even though the module is still loaded (and bring it back up again when I plug the cable back in)?

Cheers,

Ian

---

### Post by bscbrit on 2006-02-04
Install NetworkManager - it is designed to do precisely what you want!

---

### Post by itmarshall on 2006-02-04
Thanks for the tip. Unfortunately, it doesn't work with my card, as I require WPA and it only supports WEP at the moment.

I'll check their site periodically and hope that they can get WPA working soon, as it looks like everything I was hoping for...

---

