---
title: "Issues transfering m4a files to iPod Touch with Amarok"
date: 2011-03-10
forum: Multimedia Software
---

### Post by in.the.afterlight on 2011-03-10
So this may be an odd problem; I can't seem to figure out what would be causing it.

I downloaded Amarok 2.4 today and am attempting to use it to sync my music to my iPod Touch. .mp3 files transfer perfectly, but for some reason any .m4a file is being reassigned a .mp4 extension and being relegated to the 'Video' app on the iPod. I do realise that an .m4a is just .aac audio in an mp4 wrapper, but does anyone have any idea why Amarok and/or the iPod is deciding to treat them like a video instead? It's doing it both to my own ffmpeg-encouded .m4as as well as unprotected .m4as from the iTunes Store (relics of my time on Windows).

Anyone know what might be going on with this? Ubuntu 10.10 NE, Amarok 2.4, iPod Touch 2G (... possibly 3G, but I'm pretty sure it's a 2G) running firmware 4.2.1

---

### Post by nomko on 2011-03-10
Can't Rhythmbox do the same trick? I believe that Rhythmbox has a build-in ipod support....not sure, but you can give it a try.

---

### Post by in.the.afterlight on 2011-03-10
It does, but a) the syncing support with the iPod database appears to be not as good in Rhythmbox, and b) I just plain like Amarok more.

Mostly, since I haven't seen any reports of anyone else having this issue, I'm mostly assuming that it's something either I've done wrong, or that is mis-set, since it seems to be working for everyone else -- and all that aside, if it should work? I want to make it work, dag nabbit! ;)

---

### Post by rik_pi on 2011-11-29
could you fix your problem.
i am having the same issue here!

-rik

---

### Post by in.the.afterlight on 2011-11-29
@rik_pi:

It looks like it's a problem with the way Amarok handles... I think it was mime types? But it has to do with mp4 handling in general. The bug has been reported and I believe it has been assigned, so presumably it'll get worked on eventually.

---

### Post by tqft on 2012-02-02
Might get a working mp4==>ipod solution in 12.04, but for now appears no U dev's are working on this.

The problem is that libmp4v2 has been removed from 11.10 and not replaced.

[https://bugs.launchpad.net/ubuntu/+source/easytag/+bug/880625](https://bugs.launchpad.net/ubuntu/+source/easytag/+bug/880625)
"Launchpad Janitor (janitor)  wrote 25 minutes ago:  	  #4

[Expired for easytag (Ubuntu) because there has been no activity for 60 days.]
"

[https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/180549](https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/180549)
Peter Harvey (pharbar)  said on 2011-12-24:  	  #17
"
Happy Christmas to all...

I came across a page listing the availability of libmp4v2, libmp4v2-2 and libmp4v2-dev in the various Ubuntu releases. Oneiric is simply not listed, though Precise is, so I would hope that the next release will have this fixed.

See: [http://packages.ubuntu.com/search?keywords=libmp4v2](http://packages.ubuntu.com/search?keywords=libmp4v2)

I'm going to give up on this one, unless someone comes up with a solution in the meantime. Thanks for all the comments and help."
"Launchpad Janitor (janitor)  said on 2012-01-09:  	  #18

This question was expired because it remained in the 'Open' state without activity for the last 15 days."


So unless someone escalates this, we are SOL.

---

