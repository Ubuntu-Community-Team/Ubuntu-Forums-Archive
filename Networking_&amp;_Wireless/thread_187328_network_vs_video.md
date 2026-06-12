---
title: "network vs video"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by articfox on 2006-06-02
Hey all,

I've searched the forums but have not found a similar problem.  Here goes:

I have an averatec 3250:
Mobile AMD 1.66 GHz Athlon XP-M 2200+
512 mb ram
unichrome s3
vt 6102 rhine II nic

When I use the via driver my system hangs when I try to "ifconfig eth0 up", and the network does not work.  When using the vesa driver everything works fine, but I don't get acceleration.

Here is what xorg.conf looks like when using vesa:
Section "Device"
	Identifier	"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

And here is what it looks like when using via:
Section "Device"
	Identifier	"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Driver		"via"
	BusID		"PCI:1:0:0"
	Option		"EnableAGPDMA" 
EndSection

Any ideas on how to fix this?  ](*,)  Thanks in advance.

- Shane

---

### Post by thedward on 2006-06-03
Try adding

```
Option          "DisableIRQ"
```

To your device section in xorg.conf

That fixed a similar problem I had when using the wireless networking.

Let me know if it works.

---

### Post by articfox on 2006-06-03
Worked like a charm.  Thanks thedward!  For the first time in 5+ years I have everything working on my laptop!

---

