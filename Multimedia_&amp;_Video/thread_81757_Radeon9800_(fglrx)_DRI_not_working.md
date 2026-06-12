---
title: "Radeon9800 (fglrx): DRI not working"
date: 2005-10-25
forum: Multimedia &amp; Video
---

### Post by matthias_k on 2005-10-25
Hi,

the fglrx module packaged with Breezy doesn't work for me. I am always getting errors from Xorg related to DRI (on a note, DRI with the "ati" driver doesn't work either, but that's another story):
> matthias:~$ cat Xorg.0.log | grep ^\(WW\)
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) Ignoring request to load module GLcore
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): Bad V_BIOS checksum
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Specified desktop setup not supported: 8
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(EE) fglrx(0): DRIScreenInit failed!


Any ideas? ^^

---

### Post by WakkiTabakki on 2005-10-25
Sorry to be a drag dude, but there are about 6 billion posts in this forum that deals with exactly this problem...
You should really try the search function before posting... But, anyway, check out:
[http://ubuntuforums.org/showthread.php?t=76116](http://ubuntuforums.org/showthread.php?t=76116)
[http://ubuntuforums.org/showthread.php?t=65276](http://ubuntuforums.org/showthread.php?t=65276)
[http://ubuntuforums.org/showthread.php?t=75378](http://ubuntuforums.org/showthread.php?t=75378)
[http://ubuntuforums.org/showthread.php?t=80558](http://ubuntuforums.org/showthread.php?t=80558)
[http://ubuntuforums.org/showthread.php?t=77064](http://ubuntuforums.org/showthread.php?t=77064)

Good luck
/N

---

