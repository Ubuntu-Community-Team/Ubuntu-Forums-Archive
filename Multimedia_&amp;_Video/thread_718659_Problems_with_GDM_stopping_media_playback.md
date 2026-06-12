---
title: "Problems with GDM stopping media playback"
date: 2008-03-08
forum: Multimedia &amp; Video
---

### Post by maagpie on 2008-03-08
Hi, I'm getting pauses with audio and video and I've only been using Ubuntu for a couple of months so I'm not sure whats going on.

 I'm running 32 bit Gusty on an HP AMD 64 with an Nvidia graphics driver. Every time it happens I get  a 100 percent spike on the activity of the second processor. As far as I can tell this is being caused by a a sub-process of GDM called X.

I'm mostly using Totem but it doesn't seem to make any difference which package I use. I had 64 bit Gusty running at one point and got the same result.   All the codecs were installed using Automatix.

Anybody know how to fix this.

P.S. It's been several months since I stopped using Vista and Ubuntu has been a complete revelation. So just a word of thanks to everyone in the Ubuntu/Linux world.

---

### Post by kapello on 2008-03-11
well I can tell you that GDM is the login manager - that brings up the login window - and X is the 'windows' system in linux.

but I'm afraid no idea why this would be happening... is it possible the system thinks it wants to ask for your password for some reason?

---

### Post by maagpie on 2008-03-18
Thanks for the help but I've managed to track the problem down to the Nvidia driver. Apparently the most recent versions are a bit buggy. Anyway I found a workaound:

[http://ubuntuforums.org/showpost.php?p=3134000&postcount=544]("http://ubuntuforums.org/showpost.php?p=3134000&postcount=544")

And everything seems fine at the moment.

---

