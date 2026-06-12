---
title: "[bug ?] AC3 Passtrough switches PCM exclusively to analog out"
date: 2009-04-20
forum: Multimedia Software
---

### Post by Turex on 2009-04-20
Hi!

I'm able to reproduce this kind of issue: Watching movie using AC3 passtrough ( XBMC ) sometime causes PCM sounds go only trough analog output ( no PCM spdif ). This happens with and without pulseaudio

I'm however able to bypass this problem by restarting alsa with (i'm not sure if this is nessessary)
```
sudo /etc/init.d/alsa-utils restart 
```
and after that doing this magic trick:
```
cat /dev/urandom | ac3dec -R
```
Which gives this kind of output:
```
** CRC failed - skipping frame **
Using PCM device 'plug:iec958:{AES0 0x0 AES1 0x82 AES2 0x0 AES3 0x2}'
** CRC failed - skipping frame **
** CRC failed - skipping frame **
** CRC failed - skipping frame **
** CRC failed - skipping frame **

```

After "Using PCM device..." message sound works again trough spdif.
( This issue is only for PCM sound, AC3 and DTS bitsreams work all the time)

Does anyone else have this problem ? Or does anyone have real solution to the problem ?

---

