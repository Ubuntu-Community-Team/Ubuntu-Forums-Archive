---
title: "Dell 700m, multiple monitors/multiple resolutions - no joy"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by drob on 2006-07-02
Folks,

I've spent hours on this.  My 700m likes a resolution of 1280x800 on it's screen. I have a 21" iiyama vision master 503 on my desktop - the resolution  I want is 1400x1050 (which works fine under you know what).  I installed 915resolution and that got me to 1280x800.  But now I want more.  I want my iiyama to display at 1400x1050.  It can do 1024x768, it can do 1280x800 (which is of course funky) but nothing on the higher rez.  Here are some other tidbits - 

915resolution is currently set to:

MODE=auto

It has also worked at:

MODE=5c
XRESO=1280
YRESO=800

but not :

MODE=5c
XRESO=1400
YRESO=1050

My xorg.conf seems mostly to go ignored, the "screen" section has:

	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1280x800" "1024x768" "800x600" "640x480"

but when I go to the screen resolution utility I see 1280x800, 1024x768, 800x600 and 640x480.  I think I've tried everything :(.   I've read through a ton of similar posts here and everywhere else.  The closest thing I've seen is one guy who claimed to get everything working (a higher rez external monitor) by re-running the xwindows config utility and forcing it to use the external monitor when doing the video testing, but I can't figure out how to force my laptop to use the external throughout that process.

Thanks,

Perplexed

---

### Post by wpollans on 2006-07-03
Were you able to get a clear image on your external monitor at any resolution?  
I can't get a clear image on an external monitor/projector at any resolution - using 'i810switch lcd off' improves the image, but the resolution is quite low (everything appears too large)

---

### Post by drob on 2006-07-04
yes.  I can see clearly up to 1024x768.  I suggest you re-run the X-windows config and make sure that you have installed 915resolution.  The problem I'm having is getting up above 1024x768.

---

