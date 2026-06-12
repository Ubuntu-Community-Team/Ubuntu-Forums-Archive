---
title: "new to ubuntu trying to get sound to work"
date: 2009-09-12
forum: Multimedia Software
---

### Post by silentpower on 2009-09-12
so I've gone through the  sound guide and still not working. 

not sure what info you need but I have an hp tx2500 laptop and using the realtek alc268 diver.

when I type aplay -l this is what I get back:

card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v:

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Hewlett-Packard Company Device 30f1
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

followed the rest of the steps so I am really lost

any help would be appreciated
-SP

---

### Post by Favux on 2009-09-12
Hi silentpower,

Are you using Jaunty (9.04)?

If so the following line works for TX2500 users:
```
options snd-hda-intel index=0 model=toshiba position_fix=1

```
Add it to the bottom of the file "alsa-base.conf" at "/etc/modprobe.d/". Don't worry that it says Toshiba.

To edit it enter in a terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Save, close, and reboot.

Also check to see if the mixer is muted. If so make sure the sliders are up.

Hope this helps.

---

### Post by silentpower on 2009-09-13
thanks bud! that worked!:KS

---

### Post by Favux on 2009-09-13
Hi silentpower,

Good!  You're welcome.

---

