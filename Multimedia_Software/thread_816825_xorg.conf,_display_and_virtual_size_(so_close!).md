---
title: "xorg.conf, display and virtual size (so close!)"
date: 2008-06-03
forum: Multimedia Software
---

### Post by fizban9 on 2008-06-03
I'm trying to figure this out, I really am.  I understand my situation is weird.  I'm running Gutsy on an AppleTV and it's connected using hdmi to my HDTV.  It all runs great except one issue.  The desktop is bigger than the screen.

Now I've got other posts up trying to figure this problem out from different angles.  Here, I want to talk about modifying a section of the xorg.conf file.  Specifically in the "Screen" section and the "Display" subsection.  

It's an option called "Virtual."  According to the man pages this option "specifies the virtual screen resolution  to be  used."  Below is my xorg.conf file without the virtual option set.  When I boot with this I get my normal situation, where the edges of my desktop goes off the screen.

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Modelname	"Custom 1"
	# gtf 1024 768 60
	Modeline "1024"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
	Gamma	1.0
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	Option		"NoLogo"	"True"
	Option		"Coolbits"	"1"
	SubSection "Display"
		Depth	24
		Modes	"1024"	
	EndSubSection
EndSection
```

Now, if I add the virtual option, like so:  

*(The 992 and 744 are just an example.  I came up with several variations, all with the exact same result)*

```
SubSection "Display"
		Depth	24
		**Virtual 992 744**
		Modes	"1024"	
	EndSubSection
```

I get a very interesting result.  My desktop still goes off the edge of the screen, but I can move my mouse an the desktop pans with it.  Even more interesting is that the edges now match up with the edge of my TV (when I pan to them.)

So somehow, when I have the virtual option set, it properly detects the edge of my screen (though I have to pan around to see the whole desktop.)  When I don't, it doesn't.  I don't know what to do.

Does what I'm describing even make sense?

---

### Post by aeiah on 2008-06-03
yea it makes sense, although i dont know how you'd sort it out from the angle you're taking. i sorted it out using a custom modeline. this might be a problem for you unless you have a windows box lying around. at least with the nvidia drivers, sorting out overscan is really easy under windows. you can tweak the screen to fit each corner and then save it. it'll show as a weird resolution. then enter that resolution into powerstrip and copy the settings to the clipboard and paste it into a text file. it will include a linux modeline.

why, incidentally, is 1024 mentioned at the end of your xorg? this isnt an hd resolution. you should be going for 1280x720 (after sorting out the overscan i think my res is something like 1240x695) or higher if your tv is 1080p and your box can handle it.

also, if your tv can handle  [pixel mapping](http://pixelmapping.wikispaces.com) via dvi or something, you might want to use this as it'll give you a better picture at either 1366x768, 1364x768, 1360x768 or a 1080p resolution and may solve your overscanning too

---

### Post by fizban9 on 2008-06-03
> **aeiah said:**
> why, incidentally, is 1024 mentioned at the end of your xorg? this isnt an hd resolution. you should be going for 1280x720 (after 'sorting out the overscan i think my res is something like 1240x695) or higher if your tv is 1080p and your box can handle it.

Yeah, that's an interesting point and I've been trying to figure it out.  My TV is, according to the manual, 1080i.  However, if you delve deeper into the manual is says it's "PC Resolution" is 1024*768@60hz.  Then, if you delve even deeper it specifically says I have a "WXGA 1024*768p" screen.

So does that mean my tv takes 1080i input but dumbs it down to 1024*768 or does that mean that only PC's are limited by the 1024*768?  (my TV doesn't even have a VGA plug)

Like I've said, I'm exploring this issue from a lot of different angles at the same time.  One of them is an email to Philips, my TV maker, to see if they can answer that question.  I'm also asking them if can tell me the horizontal timings and vertical timings of my tv.  I bet they'll answer the first question but not the latter.

---

