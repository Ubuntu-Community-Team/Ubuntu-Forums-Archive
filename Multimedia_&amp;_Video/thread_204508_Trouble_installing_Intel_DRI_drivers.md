---
title: "Trouble installing Intel DRI drivers"
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by DiamondX on 2006-06-27
I bought a laptop recently, and it came with intel intergraded graphics, the 945GM chip to be exact. I finally (after weeks) found dri.sourceforge.net. I quickly downloaded the dri snapshot, and installed. It found all the paths fine, but heres what happened:
```
DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.freedesktop.org ]

==========================================================================

The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

```

Here is the dri.log file:
```
Makefile:173: *** Cannot find a kernel config file.  Stop.
```

I have a feeling I am very close to getting it to work. Does anyone know what happened and how to fix it? Thanks in advance.

---

