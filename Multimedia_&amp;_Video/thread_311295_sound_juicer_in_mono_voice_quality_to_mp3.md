---
title: "sound juicer in mono voice quality to mp3"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by CareySchug on 2006-12-02
OK, I followed the directions in the desktop guide and I installed gstreamer and set up the following mp3 option in sound juicer:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc ! id3mux

and it seems to work ripping a cd.  However, I want fairly low quality voice, in mono only.  I tried just adding another option to sound juicer saying

audio/x-raw-int,rate=11025,channels=1 ! lame name=enc ! id3mux

Which appears to be what audiograbber (under windows) does for low quality audio, but i get an error mesage

"Sound Juicer could not extract this CD.
Reason: Could not link pipeline"

So, is there some other way to make gstreamer do mono voice grade encoding, or is there another mp3 encoder I can use, or another ripping program?  Or has anybody gotten audiograbber to work under wine (as I could not)?

---

### Post by tigerpants on 2006-12-11
> **CareySchug said:**
>   Or has anybody gotten audiograbber to work under wine (as I could not)?

Audiograbber under WINE works perfectly well in Dapper and Edgy. Do a search on audiograbber on this forum, I made a how-to post. Post your problem here and I'll try and help.

You can drop the lame.dll into the audiograbber folder in wine and audiograbber will encode with lame no problem.

---

