---
title: "pulseaudio-0.9.10 can not compile in ubuntu 8.10"
date: 2009-03-15
forum: Multimedia Software
---

### Post by fireboxmm on 2009-03-15
Hi

I try to compile pulseaudio in ubuntu 8.10, get below errors, It is said it is problem of libtool, I downgrade it to 1.5.26-1ubuntu1, but still get the same error, Anyone know how to fix this?  Thanks a lot!



pulseaudio-dumpmodules.o: In function `pa_dump_modules':
/usr/src/pulseaudio-0.9.10/src/daemon/dumpmodules.c:140: undefined reference to `lt__PROGRAM__LTX_preloaded_symbols'
/usr/src/pulseaudio-0.9.10/src/daemon/dumpmodules.c:135: undefined reference to `lt__PROGRAM__LTX_preloaded_symbols'
pulseaudio-dumpmodules.o: In function `is_preloaded':
/usr/src/pulseaudio-0.9.10/src/daemon/dumpmodules.c:97: undefined reference to `lt__PROGRAM__LTX_preloaded_symbols'
/usr/src/pulseaudio-0.9.10/src/daemon/dumpmodules.c:97: undefined reference to `lt__PROGRAM__LTX_preloaded_symbols'
pulseaudio-main.o: In function `main':
/usr/src/pulseaudio-0.9.10/src/daemon/main.c:507: undefined reference to `lt__PROGRAM__LTX_preloaded_symbols'
collect2: ld returned 1 exit status
make[3]: *** [pulseaudio] Error 1

---

### Post by markbuntu on 2009-03-16
Why are you doing that?
Intrepid 8.10 already comes with pulseaudio 0.9.10.
If you want to get it working properly go here

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

