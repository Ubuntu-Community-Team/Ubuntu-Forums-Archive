---
title: "Capturing DV-video FireWire"
date: 2011-04-08
forum: Multimedia Software
---

### Post by thunderbirdje on 2011-04-08
Hello everyone,

I want to capture DV-video through IEE1394 (FireWire) with Kino and Ubuntu 10.10

Seems I can't capture... When I plug in the camera there is no hot plug message (if there should be one? I've read it should...).

The DV-out on the camera is enabled ;-) There is no option to enable/disable the port in my BIOS.

Some information:

```
a~# lspci | grep 1394
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
```

Hope there are some command to check?

Thank you

---

### Post by thunderbirdje on 2011-04-29
Found the solution: I replaced the (cheap) FireWire cable with a more expensive one and it worked like a charm! So great :-)

---

