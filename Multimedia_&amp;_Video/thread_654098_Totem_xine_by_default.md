---
title: "Totem xine by default"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by james_steward on 2007-12-30
Hi folks,

Recently I installed 2 7.10 virgin systems, one at work, and one for my Mum.  In both cases the following occurs.

Try to play an mp4.  
Totem starts and says it needs plugins for mp4 files.  
After a search, it seemed that the GStreamer plugins were the way to go. 
I install every GStreamer plugin, including "bad" ones.
Try to play the mp4 - same problem.

I looked at the Totem website, and it says it can use xine or GStreamer plugins, but I guess not both at once, as you install for one or the other backend.  Great, so which Totem is installed on my system?  You guessed it - Totem (xine backend).

The tricky bit is that in Add/Remove, there are 2 Movie Player entries, both install Totem, but the second doesn't say so in the heading, just "Movie Player", whereas the first is "Movie Player Totem (xine backend)"

So why is Totem for xine installed by default?

Shouldn't the 2 variants be clearly distinguished?

Oh, and when I tried to install some xine plugins, it said there were non for my i386 platform...

Cheerio.

---

### Post by pay on 2007-12-30
```
sudo aptitude remove totem-xine
sudo aptitude install totem-gstreamer
```To get back to gstreamer.

---

### Post by james_steward on 2007-12-30
In Add/Remove I simply selected "Movie Player" (which is Totem for GStreamer).  It removed "Movie Player Totem (xine backend)" and installed "Movie Player" nicely.  Now it makes use of the gstreamer plugins I had previously installed.

The package manglement is the easy bit.  The fact remains that the package names from Add/Remove are not clear enough, and why is totem-xine installed by default?  The documentation I read about getting plugins for various formats spoke of GStreamer plugins.  There is a lack of consistency here.

[https://help.ubuntu.com/7.10/musicvideophotos/C/codecs.html](https://help.ubuntu.com/7.10/musicvideophotos/C/codecs.html)

and

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) suggests ubuntu-restricted-extras, which installs gstreamer plugins according to Add/Remove information.

The upshot is, I got it working, but only after some head scratching and searching.

My message is that there is documentation inconsistencies that some kind folk may be able to improve.

---

