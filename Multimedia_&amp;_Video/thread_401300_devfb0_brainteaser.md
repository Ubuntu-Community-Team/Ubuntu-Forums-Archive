---
title: "/dev/fb0 brainteaser"
date: 2007-04-04
forum: Multimedia &amp; Video
---

### Post by keithjr on 2007-04-04
I have a novel little question regarding the framebuffer device.

For a class project I'm trying to get fbdoom to run on a development board.  fbdoom is a port of the original doom engine which runs on the framebuffer device (/dev/fb0 by default) instead of an X server.  I'm attempting to test it on my own machine (Edgy x86), and run into this problem at runtime:

```

Error: Unable to open framebuffer

```

I am running this in the recovery mode to keep X from sucking up the device, which does in fact exist:

```

crw-r--r-- 1 root root 29, 0 2007-04-04 12:27 /dev/fb0

```

but if I try to interact with the device...I get this:

```

$ cp /dev/fb0 myfile
cp: cannot open `/dev/fb0' for reading: No such device

```

Sooooo do any of you know how to utilize the framebuffer device AFTER boot-up?

---

### Post by aethra on 2007-12-27
try sudo modprobe vesafb

---

