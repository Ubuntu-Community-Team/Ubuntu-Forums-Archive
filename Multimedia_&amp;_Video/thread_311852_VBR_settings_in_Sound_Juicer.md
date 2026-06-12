---
title: "VBR settings in Sound Juicer?"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by klato on 2006-12-03
I'm about to rip some of my music collection, but I haven't done this in quite a while. When I used Windows, I usually used LAME with I think a VBR preset standard that was sort of like a "default, good quality, good size" VBR setting. Does anyone know how to enable that on Sound Juicer? Right now my gstreamer pipeline says this:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=4

I'm not sure that this is the preset I'm describing though. I've done some forum searching about it, but I'm getting a little confused with all the options.

Thanks!

Update: OK after some more searching I think I found the setting: preset=standard

Although ripping is pretty slow (only at 2.6x)

---

### Post by logos34 on 2006-12-04
Shouldn't be so hard to find a pipeline setting that works, right?
Sound Juicer Help has a section at the end about mp3 settings, but the gstreaner pipeline doesn't work.  And boy do you have to seach the web for one that does.  Here's what works for me:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=4 vbr-quality=x ! id3v2mux

where 'x' in vbr-quality = any integer from 0-9.  I use 2, which gives me a result identical to '-V 2 --vbr-new' or 'alt-preset standard' (ie 192kbps average).  

Note: it's erroneously tagging the files "32kbps, CBR" for some reason (see properties>audio tab), but if you open one in xmms or audacious you'll see the bitrate bounce around like it should in vbr.

Hope that helps you.

---

