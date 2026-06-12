---
title: "Request: edid.bin for DGM (Digimate) L-1431W LCD Monitor"
date: 2010-02-02
forum: Multimedia Software
---

### Post by sandrogalli on 2010-02-02
So it appears that the edid has corrupted on my monitor and /var/log/Xorg.0.log returns the following:

```
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
```

I am able to set the resolution for this monitor but as it is receiving no edid, the alignment is way off, maybe 2-3 inches and beyond the capability of the monitors auto adjust to fix.

I am aware that it is possible to set a UseCustomEDID line in xorg.conf and would greatly appreciate it if someone with the same monitor would be kind enough to dump the edid.bin for me so I can continue using this monitor, at least in linux.

The monitor is a: DGM (Digimate) L-1431W 15" Widescreen LCD Monitor.

Here is a link to the manufacturers website for reference:

[HTML]http://www.digimate.co.uk/download/L-1431W-User%20manual-V1.0.pdf[/HTML]
Many thanks in advance,

San

---

