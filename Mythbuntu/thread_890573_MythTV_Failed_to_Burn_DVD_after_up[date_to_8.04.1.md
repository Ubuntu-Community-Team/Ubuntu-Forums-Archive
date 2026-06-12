---
title: "MythTV Failed to Burn DVD after up[date to 8.04.1"
date: 2008-08-15
forum: Mythbuntu
---

### Post by neoneddy on 2008-08-15
I upgraded to 8.04.1 didn't reboot, burned a few dvd's then ended up rebooting, and now I get this error in my log files.

I used a fresh DVD - and used a cut list, and had it compress the files to fit on the dvd, it might have been a close fit, but none the less the Archive Utility said it would fit.

From mythburn.log
```
Finished  dvdauthor
Burning ISO image to /dev/dvd
growisofs -dvd-compat  -Z /dev/dvd -dvd-video -V "NASCAR Countdown" /tmp/work/dvd
Running growisofs to burn DVD
Executing 'genisoimage -dvd-video -V NASCAR Countdown /tmp/work/dvd | builtin_dd of=/dev/dvd obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
:-( /dev/dvd: 2297888 blocks are free, 2306165 to be written!
:-( write failed: No space left on device
genisoimage: Broken pipe. cannot fwrite 2048*2
------------------------------------------------------------
ERROR: Failed while running growisofs.
Result 156, Command was: growisofs -dvd-compat  -Z /dev/dvd -dvd-video -V "NASCAR Countdown" /tmp/work/dvd
Please check the troubleshooting section of the README for ways to fix this error
------------------------------------------------------------

chmod: changing permissions of `/tmp/': Operation not permitted
chmod: changing permissions of `/tmp/.ICE-unix': Operation not permitted
chmod: changing permissions of `/tmp/.X11-unix': Operation not permitted
chmod: changing permissions of `/tmp/.X11-unix/X0': Operation not permitted
chmod: changing permissions of `/tmp/mythtv_ddp_7UAvTg': Operation not permitted
chmod: cannot read directory `/tmp/mythtv_ddp_7UAvTg': Permission denied
chmod: changing permissions of `/tmp/tmp.RAMccb6054': Operation not permitted
chmod: changing permissions of `/tmp/.X0-lock': Operation not permitted
Terminated
```

Any thing you guys or ladies might know of?

---

