---
title: "nvclock trouble"
date: 2006-02-17
forum: Multimedia &amp; Video
---

### Post by chimera on 2006-02-17
I installed nvclock yesterday and managed to overclock my 6600GT 3d clocks to 550mhz (core clock speed), 1100mhz (memory clock speed) using the coolbits3d backend. After I rebooted my computer, the clock speeds were set back to default (500, 900), and I can't set them back. This happens:

```

chimera@HOMEPC:~$ nvclock -b coolbits3d -n 550 -m 1100
Requested memory clock:         1100.000 MHz
Requested core clock:           550.000 MHz

Adjusted Coolbits 3D clocks on a nVidia Geforce 6600GT
Memory clock:   900.000 MHz
GPU clock:      500.000 MHz

chimera@HOMEPC:~$

```

Does anyone know what could be the cause of this? I tried purging and reinstalling nvclock with apt-get, which didn't yield any results.

---

