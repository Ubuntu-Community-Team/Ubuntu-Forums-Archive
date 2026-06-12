---
title: "xv video not working"
date: 2009-01-26
forum: Multimedia Software
---

### Post by djuniah on 2009-01-26
I'm trying to get xv working with gmplayer.  I have had it working before, but since i upgraded to 8.10 i've had issues.  

if i run xvinfo i get:
```
X-Video Extension version 2.2
screen #0
 no adaptors present

```

Here is a section from xorg.conf (i added the xv part myself, but it didnt work):
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
	Option "xv"
EndSection

---

