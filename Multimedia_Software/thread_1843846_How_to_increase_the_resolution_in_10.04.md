---
title: "How to increase the resolution in 10.04?"
date: 2011-09-14
forum: Multimedia Software
---

### Post by tonysonney on 2011-09-14
Hi All,
       I am using 10.04 64bit Ubuntu. The problem I am having is while using dual monitors.
1) NEC MultiSync LCD (1280x1024) (Supported by Ubuntu).
2) Dell P2211H (1920x1080) (Not supported in System->Preferences-> Monitor->Resolution).

The graphics card I am having is 

```
lspci -v | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68f9
```


```
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68f9
        Subsystem: Dell Device 2126
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at e1420000 (64-bit, non-prefetchable) [size=128K]
        I/O ports at 3000 [size=256]
        Expansion ROM at e1400000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel modules: fglrx
```

I wonder the driver is able to open the device from the above output 
```
Capabilities: <access denied>
```

I am connecting the monitors using DVI to VGA splitter.

How do I fix this? Please help.

Thanks,
Tony

---

