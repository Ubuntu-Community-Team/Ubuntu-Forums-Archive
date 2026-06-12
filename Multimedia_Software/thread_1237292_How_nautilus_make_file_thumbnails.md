---
title: "How nautilus make file thumbnails?"
date: 2009-08-11
forum: Multimedia Software
---

### Post by Barafu Albino Cheetah on 2009-08-11
PLease, give me a link to some info on how does nautilus create thumbnails to files? I have to make adjustments to the process.

---

### Post by quixote on 2009-08-12
The only easy thing to change is thumbnail size. Edit > Preferences, Views tab and set icon size.  Also, under Preview tab, you can limit which files it will try to make thumbnails of: eg only local files smaller than 5MB, or all files, including those on any networked drives even if they're as big as 100MB, and so on.  It's a good idea to be a bit stingy about thumbnails, because they can take up preposterous amounts of space.  (Check properties on your ~/.thumbnail directory....)

If you want something more advanced than that, I'm not even sure where you start.  Gnome makes customization way harder than it needs to be.  I recently found [this web site]("http://orford.org/gtk/") that talks about altering gtkrc, but haven't tried any of that stuff yet.

---

### Post by Barafu Albino Cheetah on 2010-06-05
Bump. Still wondering on the thing. I want to write a python app that will create thumbnails for given file type.

---

### Post by Ohrer on 2010-06-05
For video thumbnails Nautilus uses Totem and the package totem-video-thumbnailer

---

