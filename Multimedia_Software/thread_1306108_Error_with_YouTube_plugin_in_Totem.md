---
title: "Error with YouTube plugin in Totem"
date: 2009-10-30
forum: Multimedia Software
---

### Post by Aero-Z on 2009-10-30
Hello,

I tried to use the YouTube plugin with Totem. Searching videos works. When I double click a HD YouTube video then nothing happens. When I double click a normal video I get following error:
```
GStreamer encountered a general supporting library error.
```

Any ideas how to fix it?

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-30
I sucessfully reproduced the problem.
Does anyone have an idea why this is happening ?

---

### Post by blur xc on 2009-10-30
Mine does it too.  I was actually getting ready to post my own thread regarding this problem...

I have all the gstreamer packages installed as well.

I'm 99% certain I have all of these installed (according to Ubuntu Kung Fu):
```
GStreamer extra plugins
GStreamer ffmpeg video plugin
Ubuntu restricted extras
GStreamer plugins for mms, wavpack, quicktime, musepack
GStreamer plugins for aac, xvid, mpeg2, faad
GStreamer fluendo MPEG2 demuxing plugin

```BM

edit- actually, I'm not 100% certain I'm getting the same exact error, I'll verify when I get home...

---

### Post by mCion on 2009-11-07
same problem here...

---

### Post by ram130 on 2009-11-08
same here for all youtube videos in totem. What the sense build support for youtube when it doesn't work?? I mean come on.

---

### Post by Donnw on 2009-11-08
This worked until I upgraded to Karmic. now I get the same error. If totem is run from command line I get this error:

** (totem:3939): WARNING **: Couldn't find the t param of entry (null) or its FLV URI.
** Message: Error: GStreamer encountered a general supporting library error.
gstffmpegdemux.c(1243): gst_ffmpegdemux_open (): /Gst playBin2: play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/ffdemux_swf:ffdemux_swf0:
Input/output error

---

### Post by br0t on 2009-11-08
the bug is reported here: [https://bugs.launchpad.net/gstreamer/+bug/459423](https://bugs.launchpad.net/gstreamer/+bug/459423)

currently there is an update for karmic in the karmic-proposed package-source, which works fine for me and others, see:
[https://bugs.launchpad.net/gstreamer/+bug/459423/comments/47](https://bugs.launchpad.net/gstreamer/+bug/459423/comments/47)

someone also prepared a patch for jaunty, but it still needs acknowledged to get into the jaunty-proposed package-source:
[https://bugs.launchpad.net/gstreamer/+bug/459423/comments/68](https://bugs.launchpad.net/gstreamer/+bug/459423/comments/68)

if you want use the proposed updates take a look at the following how to:
[https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

with some patience a public fix should be available soon through the official/stable package-sources..

---

### Post by blur xc on 2009-11-09
> **br0t said:**
> the bug is reported here: [https://bugs.launchpad.net/gstreamer/+bug/459423](https://bugs.launchpad.net/gstreamer/+bug/459423)

currently there is an update for karmic in the karmic-proposed package-source, which works fine for me and others, see:
[https://bugs.launchpad.net/gstreamer/+bug/459423/comments/47](https://bugs.launchpad.net/gstreamer/+bug/459423/comments/47)

someone also prepared a patch for jaunty, but it still needs acknowledged to get into the jaunty-proposed package-source:
[https://bugs.launchpad.net/gstreamer/+bug/459423/comments/68](https://bugs.launchpad.net/gstreamer/+bug/459423/comments/68)

if you want use the proposed updates take a look at the following how to:
[https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

with some patience a public fix should be available soon through the official/stable package-sources..

So it will get fixed through the normal update process?  ie. I don't have to *do *anything?

BM

---

### Post by Donnw on 2009-11-09
The unsupported update fixed the problem

Thanks

---

### Post by triva911 on 2010-08-06
> **Aero-Z said:**
> Hello,

I tried to use the YouTube plugin with Totem. Searching videos works. When I double click a HD YouTube video then nothing happens. When I double click a normal video I get following error:
```
GStreamer encountered a general supporting library error.
```Any ideas how to fix it?

Download video and audio plugins GStreamer from Software Center

---

### Post by lidengdeng on 2011-05-29
> **triva911 said:**
> Download video and audio plugins GStreamer from Software Center

Which one?

There are so many plugins for GStreamer there in Software Center...

---

### Post by spas87 on 2011-09-17
Yea got got that error 10.04 fully updated i will try to find gsreamer and see any other suggestions.

---

### Post by leilton on 2011-10-16
I have installed all of them and makes no difference whatsoever
Thought program had been around long enough for this to have been fixed by now.
Still one lives in hopes.
..

---

### Post by rbaleksandar on 2011-11-07
Using Lucid 10.04 LTS. Same problem here. Just started the player to watch some YT-videos. Haven't used this feature in quite a while. Hope they fix it soon. :KS

Greetings,
rba

---

### Post by Jbike on 2011-11-12
Can you be more specific as to which GStreamer plugins? There are 124 items that match a "GStreamer query" in the software center. 

Thanks,
Jbike

---

