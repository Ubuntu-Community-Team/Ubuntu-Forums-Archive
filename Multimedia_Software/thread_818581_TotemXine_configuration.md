---
title: "Totem/Xine configuration?"
date: 2008-06-04
forum: Multimedia Software
---

### Post by ReeRD on 2008-06-04
I've just installed totem-xine but there are very few configuration options in Totem itself. There must be more of them available. I'm interested in performance/video/audio/postprocessing options more than GUI changes. Where do I find such settings if they do exist?

One more question. Right now I have the following media related packages installed:

ubuntu-restricted-extras
totem-xine (which depends on multiple xine related packages)
totem-gstreamer (which is installed by default but I don't use it)

Do I need something else besides these to be able to play most common video/audio formats with totem-xine?

---

### Post by kostkon on 2008-06-05
> **ReeRD said:**
> I've just installed totem-xine but there are very few configuration options in Totem itself. There must be more of them available. I'm interested in performance/video/audio/postprocessing options more than GUI changes. Where do I find such settings if they do exist?
For more options you can check the file *catalog.cache* that exists in the folder
```
~/.xine/
```
Also, don't forget the Totem configuration files *totem* and *totem_config* you can find in
```
~/.gnome2/
```
> **ReeRD said:**
> One more question. Right now I have the following media related packages installed:

ubuntu-restricted-extras
totem-xine (which depends on multiple xine related packages)
totem-gstreamer (which is installed by default but I don't use it)

Do I need something else besides these to be able to play most common video/audio formats with totem-xine?
Yes, you need something else! :mrgreen:

Add the [*Medibuntu* repository]("http://medibuntu.org/") to your software sources list (instructions [here]("http://help.ubuntu.com/community/Medibuntu")) and then install the *w32codecs* package. That way you will add much more codecs that will allow you to play Windows Media, Real and many other formats.

---

### Post by ReeRD on 2008-06-05
> **kostkon said:**
> For more options you can check the file *catalog.cache* that exists in the folder
```
~/.xine/
```

That file contains some kind of xine cache. Those options aren't human readable either.

> **kostkon said:**
> Also, don't forget the Totem configuration files *totem* and *totem_config* you can find in
```
~/.gnome2/
```

There are no such files in this directory.

Actually, what I'm looking for is something similar to ffdshow configuration on Windows.

> **kostkon said:**
> Add the [*Medibuntu* repository]("http://medibuntu.org/") to your software sources list (instructions [here]("http://help.ubuntu.com/community/Medibuntu")) and then install the *w32codecs* package. That way you will add much more codecs that will allow you to play Windows Media, Real and many other formats.

Thanks, added those.

---

### Post by TryMe on 2008-06-17
Don't know if this is exactly what you want but... open terminal and type "gconf-editor" (with out the quotes) then press enter.

go into  / -> apps -> totem

---

