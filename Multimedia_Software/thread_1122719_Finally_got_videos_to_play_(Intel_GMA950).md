---
title: "Finally got videos to play (Intel GMA950)"
date: 2009-04-11
forum: Multimedia Software
---

### Post by donovan1983 on 2009-04-11
It seems to be a very common ailment with the latest video drivers included in Ubuntu for a variety of different graphics chipsets, but I finally got video playback to work on my Acer Aspire One 10" thanks to a lot of reading in the forums and trying random stuff. Previously every time I'd try to play a video I'd get a "BadAlloc" error in the terminal window. As a side benefit, Compiz now works again too. Here's my xorg.conf:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
#		Virtual	2464 900
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option "AccelMethod" "EXA"
	Option "AccelDFS" "true"
EndSection

Section "Module"
	Load	"glx"
EndSection
```

The "Virtual 2464 900" was for using an external monitor with a resolution of 1440x900. Between commenting that out and adding the "Load "glx"" stuff just started working again. Well, the "AccelMethod" and "AccelDFS" may also be helping. All I know is that it works and I won't be changing anything unless my system becomes unstable.

Hope this helps someone :)

---

