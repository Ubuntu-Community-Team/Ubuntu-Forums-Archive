---
title: "fglrx x850xt no DRI"
date: 2007-08-20
forum: Multimedia &amp; Video
---

### Post by sabbath06 on 2007-08-20
I've followed a few different tutorials for installing the fglrx drivers for my x850xt and glxinfo and glxgears always tell me that I have no direct rendering. I looked at my dmesg and it had a few things talking about fglrx. Anyone have any ideas?

```
[ 4507.856358] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[ 4507.860227] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[ 4507.860237] [fglrx] USWC is disabled in module parameters
[ 4507.860241] [fglrx] PAT is disabled!
[ 4507.861000] [fglrx] module loaded - fglrx 8.40.4 [Jul 31 2007] on minor 0
[ 4507.882661] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[ 4508.878339] [fglrx] Internal AGP is not supported in 2.6 kernel.
[ 4508.878430] [fglrx:firegl_unlock] *ERROR* Process 6757 using kernel context 0

```

---

### Post by sabbath06 on 2007-08-21
bumpity bump

---

### Post by kissg1988 on 2007-08-21
This message seems interesting for me:

```

[ 4508.878339] [fglrx] Internal AGP is not supported in 2.6 kernel.

```

I think, you should check, that agpgart is loaded correctly:

```

kissg@kissg:~$ dmesg | grep agpgart
[   43.889514] Linux agpgart interface v0.102 (c) Dave Jones
[   43.894201] agpgart: Detected SiS 630 chipset
[   43.899978] agpgart: AGP aperture is 64M @ 0xe8000000
[   67.250610] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   67.251218] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   67.251591] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode

```

Is your chipset correctly detected by agpgart?

---

### Post by sabbath06 on 2007-08-21
dmesg | grep agrgart returns

```
[   13.629713] Linux agpgart interface v0.102 (c) Dave Jones
```

---

### Post by randunel on 2008-02-06
same problem here. agp chipset not detected, no agp aperture size, nothing. Configuration:
mb chipset 875p, video ati x1950pro (agp).

---

