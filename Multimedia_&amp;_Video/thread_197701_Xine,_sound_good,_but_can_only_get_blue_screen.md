---
title: "Xine, sound good, but can only get blue screen"
date: 2006-06-16
forum: Multimedia &amp; Video
---

### Post by WADemosthenes on 2006-06-16
In xine I can get the audio to work, but all I can SEE is blue :P  When I had Vector linux they said to add: 

            Option 		"OverlayMem" "829440" 
	Option 		"XaaNoScanlineImageWriteRect"
	Option 		"XaaNoScanlineCPUToScreenColorExpandFill"

It worked on Vector, but not on xubuntu.  So I tried the xine faq and it said to add this:

	Option 		"XaaNoOffscreenPixmaps"

Still doesn't work.  What could be the problem?

---

### Post by kebajonathan on 2006-11-21
I had the same problem some time ago. this is due to your video ram. you just have to go down with your colour depth. It should work on almost any pc with 16bit...

in /etc/X11/xorg.conf:
DefaultDepth 16

---

### Post by rcarricato on 2006-12-11
Thank you so much, that was all I needed

---

