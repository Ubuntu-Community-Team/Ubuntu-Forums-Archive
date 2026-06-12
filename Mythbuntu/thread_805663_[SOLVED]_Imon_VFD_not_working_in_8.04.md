---
title: "[SOLVED] Imon VFD not working in 8.04"
date: 2008-05-24
forum: Mythbuntu
---

### Post by Trollslayer on 2008-05-24
I have a Silverstone case with an imon VFD and remote which works (apart from the pad) in 7.10.
With 8.04 the remote works the same but the VFD doesn't.
/dev/lcd0 is present and the LCDd.conf files match.
Current LCDrpoc version is 0.82.
Any suggestions?
ls usb reports the controller in both and ps reports LCDd and lircd in both.

THe /etc/modprobe.d/options file needs the following line added:
[COLOR="Blue"]options lirc islcd=0[/COLOR]
Or, if you have the iMon Pad as well:
[COLOR="Blue"]options lirc pad2keys_active=1 islcd=0[/COLOR]

---

