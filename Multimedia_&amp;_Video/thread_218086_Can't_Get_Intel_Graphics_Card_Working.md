---
title: "Can't Get Intel Graphics Card Working"
date: 2006-07-18
forum: Multimedia &amp; Video
---

### Post by ldrhcp on 2006-07-18
I'm new to Ubuntu and tried running a couple apps that try to use the graphics card (PlanetPenguin Racer and Celestia). The apps are unusably slow and my laptop gets loud--it seems that the CPU is doing all of the graphics processing. I have an Intel GMA 900 card.

I saw that glxgears -printfps should produce numbers in the thousands. I get:

```
$ glxgears -printfps
673 frames in 5.9 seconds = 114.144 FPS
684 frames in 5.6 seconds = 121.287 FPS
```

I read that the answer may be in /etc/X11/xorg.conf. This section is in it:

```
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection
```

Any ideas?

---

