---
title: "Any support to watch .nsv streams?"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by samuraiswordsman on 2006-12-03
Hey, all.

I am a relatively new user to Ubuntu, and Linux, for that matter, so go easy on me please.

I have obtained some URLs for a few SHOUTcast tv servers that i want to watch.

I have tried VLC, Mplayer, and even Xine, and all I get is the audio portion of the stream, no video whatsoever. Each player states that it has support for the .nsv format, yet nothing is working right. It's really driving me crazy. ](*,) 

So, is there possibly any solution to this? Can I stream the Video portion as well? Please help me out.

-- Samurai.

---

### Post by adamkane on 2006-12-03
Post a link, so we can try it out. 

You tryin' to make this difficult?

---

### Post by samuraiswordsman on 2006-12-03
sorry about that.... 

The one I was gonna test it out on is Desync.com : Hellsing . 

Here's the URL. Try it for yourself and you'll see what I'm talking about.

[http://64.157.15.135:8000;stream.nsv](http://64.157.15.135:8000;stream.nsv)

Go to VLC (or whatever you use) -> File -> Open Network Stream -> Copy & Paste the URL into the corresponding field and hit OK.

The Audio is all that plays. No Video.

---

### Post by CarpKing on 2006-12-03
All three of those programs do support nsv streams, which is why you can connect at all.  The problem is the video codec used to encode the stream.  That stream uses the VP6 codec, which is not well-documented.  However, I get audio and video in both mplayer and Totem-xine.  I believe I've read that VLC now supports this codec as well, but the one in Ubuntu doesn't seem to.  Are you sure you have win32codecs installed?  Maybe try:
```
mplayer http://64.157.15.135:8000
```
from a terminal and see what happens.

---

### Post by samuraiswordsman on 2006-12-03
I copied and pasted what you told me to into the terminal and It played the audio portion of the stream through the terminal.
I couldn't copy the code it gave back that was in the terminal for some reason, so I could show you what exactly happened, But I did notice that it said things like: "Video = none" , "Vdecoder failed" and "missing library" in numerous places...

So, I'm pretty positive that I lack win32 codecs, or at least some of them, as you suggested, CarpKing. Now, all I have to do is get these codecs and install them. Do you know if i can get them through Synaptic / Add/remove applications? or do I have to manually download and install them?

---

### Post by samuraiswordsman on 2006-12-03
sorry -- Double post.

---

