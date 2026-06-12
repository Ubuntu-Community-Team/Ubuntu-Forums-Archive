---
title: "Ubuntu 10.04 LIRC IMON VFD"
date: 2012-01-05
forum: Multimedia Software
---

### Post by dkenny on 2012-01-05
All
I am having no end of problems trying to configure LIRC to work. I have read multiple threads, both here and elsewhere, but still cannot get this to work. Any help would be appreciated.

I'm running Ubuntu 10.04

Here is my Imon device identifer:
```
lsusb | grep "SoundGraph"
Bus 005 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
```

I have installed LIRC
```
sudo apt-get install lirc
```

If I configure LIRC to use the "Soundgraph iMON PAD IR/VFD" then the remote will not work. I have checked this use the irw command.

I have done some further testing to try to isolate the issue(s), by using an old MS IR receiver as a substitute for the IMON. This is where is gets stranger.
If I connect the MS IR unit and run```
sudo dpkg-reconfigure lirc
```this time selecting the "windows Media Center Transceiver/Remotes (all)" option then I do see commands being passed when I run irw. So it would appear the LIRC is functioning properly at least...

BUT, if I reboot, irw does not get any commands.
Even if I run ```
sudo service lirc restart
``` I still do not see any commands being received by irw.

If I rerun dpkg-reconfigure then restart LIRC, then I do see results in irw.

So it looks like I have issues with both LIRC for MS recevier and for IMON.

Appreciate any help you can give.


Thanks
Declan

---

### Post by dkenny on 2012-01-09
Shameless bump....

---

