---
title: "Playing APE (Monkey Audio) in Feisty"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by unimatrix on 2007-06-28
Is there any way to play .ape format in K/Ubuntu Feisty?
From what i've read on other forums GStreamer-0.8 supported APE, but Feisty includes GStreamer-0.10 by default, which doesn't yet decode apes.
In older releases there was an xmms-mac package that allowed XMMS to play APE, but this was removed before Feisty too. I found some packages, but they were all x86 while I would need a 64bit version.
Any other ideas? Thanks

---

### Post by unimatrix on 2007-06-28
There seem to have been 2 websites containing a decoder: [http://sourceforge.net/projects/mac-port/]("http://sourceforge.net/projects/mac-port/") and [http://supermmx.org/linux/mac/]("http://supermmx.org/linux/mac/")
But they're both dead now.

There is a libmac codec in this repo: [http://morgoth.free.fr/ubports/]("http://morgoth.free.fr/ubports/") but I'm not really sure what to do with it. Not to mention there's no AMD64 version...
And this is another tool for "processing compressed WAVE data" (whatever that means) [http://etree.org/shnutils/shntool/]("http://etree.org/shnutils/shntool/")

What I did was to install the Fedora Core 3 mac package I've found here [http://rpmfind.net/linux/rpm2html/search.php?query=mac](http://rpmfind.net/linux/rpm2html/search.php?query=mac) using "alien" to convert it to a .deb
then I converted the .ape file as so:
> mac audiofile.ape audiofile.wav -d
It was a simple task, but It could be even simpler If I could find the xmms-mac package (or at least the source) somewhere.

If anyone knows a link, please don't hesitate to post.

---

### Post by SeaJey on 2007-06-28
audacious-mac from 
deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) feisty-backports main 
seems to be a  working solution to play album.ape + album.cue

But I don't like Audacious, I'm in love with amaroK.

Anybody knows how to make amaroK to work with this format?

---

### Post by unimatrix on 2007-06-28
Yeah, it works, but only for x86 architectures.
Amarok is supposed to play .ape if you change its engine from xine to gstreamer (but it has to be version 0.8 ). Haven't tried that yet, because for some reason I can't use any other engine than xine, even though I've installed the amarok-engines package.

---

