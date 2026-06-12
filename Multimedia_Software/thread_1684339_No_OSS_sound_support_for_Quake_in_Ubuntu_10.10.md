---
title: "No OSS sound support for Quake in Ubuntu 10.10"
date: 2011-02-09
forum: Multimedia Software
---

### Post by darkhelmetchris on 2011-02-09
Call me crazy, but I still like old original Quake.  For some reason, in Ubuntu 10.10 I can no longer get audio to work.  It seems to me that there is now some incompatibility with OSS-based apps and the new pulseaudio.

In Ubuntu 9.10, I used this little trick to get sound to work in Quake (ProQuake):
```
$ sudo echo "quake_x11 0 0 direct" >/proc/asound/card0/pcm0p/oss
```However, in Ubuntu 10.10, the above command now gives me the following error:
```
bash: /proc/asound/card0/pcm0p/oss: No such file or directory
```Does anyone know what I should be doing differently to get older applications that use OSS sound to work with pulseaudio?

Additional details:
I have downloaded the most recent source for ProQuake, installed all the dependancies, and got it all compiled quite nicely.  ProQuake does run just fine, IF I pass the -nosound option at run time.  If I do not specify -nosound then I simply get a segmentation fault.  Testing the same binary against Ubuntu 9.10 works just fine with sound.

---

