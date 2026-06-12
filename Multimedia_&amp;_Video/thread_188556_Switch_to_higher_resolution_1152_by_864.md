---
title: "Switch to higher resolution: 1152 by 864"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by xpix on 2006-06-04
Hello guys (first post here  :D ),

I would like to change my screen resolution. 

For me:

1024 x 768 is to small (Refresh Rate: 85Hz)
1280 x 1024 has a low refresh rate: 60Hz

So I would like to change it into: 1152 by 864 (I use the same for W XP)

Which is the most recommended solution

PS: 
1152 by 864 does not appear in System/Scree Resolution
I use GForce Mx 440

Thx

---

### Post by JoWilly on 2006-06-04
You need to add "1152x864" in the front, just before the other modes, in the screen section of your /etx/X11/xorg.conf file

SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
EndSubSection

---

### Post by xpix on 2006-06-04
[QUOTE=JoWilly]You need to add "1152x864" in the front, just before the other modes, in the screen section of your /etx/X11/xorg.conf file

SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
EndSubSection[/QUOTE]

thx, it worked(after i restarted X)
..but now I have a little problem with the desktop
[IMG]http://www.bikeattack.ro/Screenshot.jpg[/IMG]
In the upper right corner it does not look good if I use transparency on the style of the top panel. If I remove transparency it is OK.

Any idea why?

---

### Post by JoWilly on 2006-06-04
[QUOTE=xpix]thx, it worked(after i restarted X)
..but now I have a little problem with the desktop
[IMG]http://www.bikeattack.ro/Screenshot.jpg[/IMG]
In the upper right corner it does not look good if I use transparency on the style of the top panel. If I remove transparency it is OK.

Any idea why?[/QUOTE]

Hmm.. this looks like a bug.

Please post a bug report on lauchpad to inform the developers (search through the bugs first).

---

