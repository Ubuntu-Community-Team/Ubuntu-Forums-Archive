---
title: "Tearing with ati drivers"
date: 2006-06-22
forum: Multimedia &amp; Video
---

### Post by preserved on 2006-06-22
After succesfully installing the new drivers I have gotten terrible tearing in ubuntu. Even scrolling in firefox causes tears(?) and I have to change focus for it to update.

fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.5814 (8.25.18)

I've also attached my xorg.conf.
[ATTACH]11643[/ATTACH]
I really need help with this issue. Damn it's annoying.

---

### Post by evil_elman on 2006-06-22
In general, I've got the same issue as you have. Not as bad it seems, but still roughly the same symptoms.

FireFox, Thunderbird and OpenOffice are the worst (the more text, the worse it is)...

Make sure that the refresh rate for the screen you're using is set correctly.

I notice that it in the following section:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection
```

The 'HorizSync' and 'VertRefresh' are set to intervals of values rather than precise values. I changed this manually to 60 for the Vertical Refresh rate on my laptop screen and got slightly better performance. I haven't changed the horizontal sych but if my memory serves me right there should be a way of calculating this depending on resolution and vertical refresh rate.

Look in the documentation of the screen (if available) for both those values at the specified resolution you're using to see if you can set it precisely. Most computer monitors have this information in my experience but laptop screens usually being an exception...

---

### Post by preserved on 2006-06-22
Tried it but to no avail. But it is strange because the top and the bottom seem alright, it is only in the middle the tearing appears.

---

