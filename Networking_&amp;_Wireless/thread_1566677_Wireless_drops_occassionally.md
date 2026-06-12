---
title: "Wireless drops occassionally"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by alienpotato on 2010-09-02
I'm running 9.10 on a desktop that connects to my network using a PCMCIA wifi card plugged into a PCI cardbus adapter.  Sometimes, (it seems to be when too much data has gone over the card), I lose connectivity.  nm-applet still shows me connected but I can't even get to my router (ping or gui).  I use ndiswrapper for the driver.

If I unplug the PCMCIA card and then plug it back in I get going again.  My questions are:

1) Anyone have an idea why this might be happening?

2) Is there a way in software for me to unload and reload the wifi card?

Any and all suggestions appreciated!
Cheers,
Sean

---

### Post by Cabalbl4 on 2010-09-03
does 
```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```
help when the card is not working?
(wlan0 is the interface, may vary)

Btw, you may try to load/unload wireless driver via modprobe
```
sudo modprobe -r yourdriver
sudo modprobe yourdriver
```

---

### Post by alienpotato on 2010-09-03
Thanks for the reply,

Not sure about the ifconfig, I will try that!  I was using ifdown/ifup which weren't working for me. Or I would use nm-applet to disable networking and then re-enable but I was having the same problem when it comes back.

If I try ```
modprobe -r ndiswrapper
``` my system hangs and I have to reboot, this happens even if I try it just after a reboot.

When I lost connectivity a few minutes ago, I looked at the router, it sees me as up but can't ping me.  Same from the desktop, I get dest. host unreachable trying to ping the router but I am showing as connected to the wifi network.

I had to physically eject and then re-insert the wifi card to fix the problem.

---

