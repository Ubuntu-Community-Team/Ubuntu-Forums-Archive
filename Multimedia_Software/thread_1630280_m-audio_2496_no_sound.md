---
title: "m-audio 24/96 no sound"
date: 2010-11-24
forum: Multimedia Software
---

### Post by blackvd on 2010-11-24
Have a m-audio 24/96 that is seen but not making sound. Original install it worked but had bad crackling. After changing Envy24 Control Setting > Hardware settings > Master Clock to S/PDIF it will no longer play sound and will not switch back to 44100.

```
$ cat /proc/asound/cards 
 1 [M2496          ]: ICE1712 - M Audio Audiophile 24/96
                      M Audio Audiophile 24/96 at 0xbf00, irq 18
```

Originally had to apply the patch here to get it to work at all:

[http://https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/141]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/141")

Anyone else have this issue sorted out yet? Seems the latest kernel isn't seeing the on-board sound either as it worked fine with previous version.

Thanks.

---

### Post by cchhrriiss121212 on 2010-11-25
> After changing Envy24 Control Setting > Hardware settings > Master Clock to S/PDIF it will no longer play sound and will not switch back to 44100
I had this once, a reboot allowed me to switch back to 48KHz. 

That fix you have seems a little complex, try following the setup in [this comment]("http://ubuntuforums.org/showpost.php?p=9107332&postcount=2") (you will need to change the model to the 24/96).

---

