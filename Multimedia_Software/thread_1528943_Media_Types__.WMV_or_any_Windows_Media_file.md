---
title: "Media Types :: .WMV or any Windows Media file"
date: 2010-07-11
forum: Multimedia Software
---

### Post by ve2 on 2010-07-11
Ok so I have a ton of .WMV files. How do I get them to play? Totem?? Where is this application they call Totem? I can't see it - but I have installed it... any ideas or help on this. I would figure by now 10.04 would allow to play any media file..help!

---

### Post by vfiz on 2010-07-11
Totem is "Movie Player" (under Applications > Sound & Video > Movie Player).  Open it, and click on Help > About to see its full name.

The reason .wmv files won't play out of the box is that they're a proprietary format.  Since they aren't open source, Ubuntu doesn't ship them with the standard desktop distribution.  Same thing goes for Flash and other closed-source programs and drivers.

The first thing you want to do is make sure that you've got the Multiverse repository enabled.  Open Ubuntu Software Center.  Click on Edit > Software Sources.  On the first tab ("Ubuntu Software"), make sure that the fourth check box is checked ("Software restricted by copyright or legal issues (multiverse)").

Then, try to open your file in Totem ("Movie Player").  If it can't play it, it should start a wizard that will help you install the appropriate codecs.  You'll probably have to go through the wizard twice as it installs different codecs.  Once Totem is happy, your video should start playing.

Here are some other options you might want to know about:

1) Install VLC.  It's a barebones media player that can play pretty much anything you throw at it out of the box.

2) Install Ubuntu Restricted Extras.  You can search for it in Ubuntu Software Center.  It's a package that installs all sorts of copyright restricted packages that make life easier (like Flash, TrueType, and Java).  

3) Check out Medibuntu ([http://medibuntu.org/]("http://medibuntu.org/")).  It's a repository that has a bunch of stuff for media.  If you install that repository, you can install w32codecs or w64codecs, depending on whether you're running a 32-bit or 64-bit system.  That package has the codecs for pretty much any windows media format.

---

