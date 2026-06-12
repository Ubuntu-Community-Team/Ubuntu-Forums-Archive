---
title: "Poor frame rates with ATI proprietary drivers."
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by randomusername on 2006-06-03
Hi all, 

I just installed the release version of  6.06 and have been having problems 
getting hardware acceleration on my Radeon 9800 working correctly.

Yes, i know - ANOTHER ATI issue. But this one is a bit different, I promise! :D 

I have installed the proprietary ATI drivers using the method shown in the
BinaryDriverHowto/ATI at : [https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2")

fglrxinfo shows that the drivers are installed and running:
```
randomusername@systemx:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

lsmod shows the fglrx module running:
```
randomusername@systemx:~$ lsmod | grep fglrx
fglrx                 388908  8
agpgart           34888  2 fglrx,intel_agp

```

Xorg.0.log shows direct rendering is enabled:
```
randomusername@systemx:~$ grep DRI /var/log/Xorg.0.log
(II) Loading extension XFree86-DRI
(==) fglrx(0): NoDRI = NO
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): [DRI] installation complete

```

But despite this, I am still getting the same frame rates in openGL apps
as I was using the standard VESA drivers.

Has anybody got any ideas as to what I need to do to get things up to
speed?

- Random

---

