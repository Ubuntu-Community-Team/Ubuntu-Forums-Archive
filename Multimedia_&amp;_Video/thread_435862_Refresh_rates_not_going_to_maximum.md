---
title: "Refresh rates not going to maximum"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by CodeCat on 2007-05-07
I'm having trouble with my nVidia FX5200 card with iiyama LS902UT monitor. I've seen that there are lots of people having trouble with display modes, refresh rates, etc. etc. and it seems I'm no exception.

The monitor is capable of 1152x864@100, which was my normal working mode in Windows. But no matter what I try, I can't get it to work in Ubuntu 7.04. The Screen Resolution changer tool just won't go any higher than 85Hz at that resolution. I added the necessary lines in xorg.conf:

```
Section "Monitor"
	Identifier	"LS902UT"
	Option		"DPMS"
	HorizSync	30-96
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"LS902UT"
	DefaultDepth	24
	[...]
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

But even then it wouldn't go any higher than 85Hz. Then I tried enabling the restricted nVidia drivers and that only made it worse. With the restricted driver it only wanted to do 1152x864@60 or even lower. And I ended up with all kinds of strange display modes, such as 640x480 at 101, 102 and 103 Hz (right...?). 1600x1200 was even listed twice. The monitor doesn't support autodetection, so none of that helped. The xorg configuration tool didn't do much to help either (except provide me with the list of resolutions as shown above).

Right now I'm working with the nVidia drivers off again, since at least now I can use 85Hz. But since I definitely want to run 3D apps this is only a temporary solution...

---

### Post by organica on 2007-05-07
You need to set up your xorg.conf file to match your monitor specs.  Check this out and match the file with what your monitor manufacturer says:

[http://iiyama3.gingco.net/internat/hu/pages/produkte/crt_int.php3?id=LS902UT](http://iiyama3.gingco.net/internat/hu/pages/produkte/crt_int.php3?id=LS902UT)

Pay attention to the resolution settings.

---

### Post by CodeCat on 2007-05-07
That seems like a list of commonly used resolutions, but it's definitely not a list of everything the monitor supports. The resolutions I put in xorg.conf all work, I tried them all out.

The thing is, Windows can go to 640x480@160Hz fine, which is supported according to that page. But Ubuntu (with nVidia restricted drivers disabled - enabled it only gets worse) sticks at 640x480@85Hz and won't show any higher rates in the list for 640x480. The same happens to all resolutions where the monitor supports 100Hz and higher.

---

