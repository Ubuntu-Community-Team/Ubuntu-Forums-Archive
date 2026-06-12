---
title: "Which gnome part reads mp3 librarys?"
date: 2011-02-03
forum: Multimedia Software
---

### Post by EricDHH on 2011-02-03
Maybe a simple question, im not sure what is running behind the curtain.

banshee
guayadeque
gnomemusicbrowser
rhythmbox

are doing the same thing with my 14k mp3 library. They all dupe exactly the same files with every full rescan of the existing music library. So i guess they all use a gnome system part for this job and there is a bug inside this part. I want to file a bug against this part but don't know the name.

Eric

---

### Post by Yellow Pasque on 2011-02-03
> **EricDHH said:**
> 
banshee
guayadeque
gnomemusicbrowser
rhythmbox
All of those players use gstreamer for backend.
You might want to install the latest stable gstreamer to see if the bug has already been fixed upstream: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

