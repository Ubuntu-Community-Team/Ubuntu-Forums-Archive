---
title: "dvd unmount issue"
date: 2010-10-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by FishRCynic on 2010-10-01
there still seems to be an issue with mounting dvds.
i have been moving files from old dvds to harddrive in order
to save the files. Some of these are damaged as far as being 
completely readable. Lucid amd64 works fine, bombs on the bad discs or
doesn't load them after which ejecting is not an issue.

Maverick attempts to mount (and unfortunately somewhat succeeds)
the unreadable discs and when it fails
it "locks" the dvd reader/writer so that it will not load any further
discs (you have to manually remove the disc or eject it as root)
If a disc mounts properly it has been showing up in the Nautilus
Places menu, the improper ones do not.  If you access /media directly
the disc is there but cannot be unmounted by the user.
Opening /media as administrator allows you to eject the disc as root
which then allows normal operation.

I know this has been an issue for others before (not necessarily Maverick)
googling :

[http://www.google.com/search?client=ubuntu&channel=fs&q=linux+dvd+won%27t+unmount&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=linux+dvd+won%27t+unmount&ie=utf-8&oe=utf-8)

gives various and sundrie results.

I was curious if anyone else has noticed this in Maverick?

(Maverick amd64 updated to RC1)

---

