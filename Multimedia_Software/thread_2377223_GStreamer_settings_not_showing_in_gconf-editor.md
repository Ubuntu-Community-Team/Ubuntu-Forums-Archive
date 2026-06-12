---
title: "GStreamer settings not showing in gconf-editor"
date: 2017-11-10
forum: Multimedia Software
---

### Post by kazakore on 2017-11-10
Running Ubuntu Studio 16.04 so not core Gnome but my understand is Gnome based programs such as gstreamer should all have their settings visible/editable via gconf-editor. Been trying to follow a couple of rather ancient guides [1] [2] but there is no settings to be seen anywhere to do with gstreamer!

I can do a test play through the module no problem with the command:
gst-launch-1.0 audiotestsrc ! jackaudiosink
so gstreamer is definitely installed and have the correct pluings.

How can I set gstreamer's default settings?

[1] [http://jackaudio.org/faq/gstreamer_via_jack.html](http://jackaudio.org/faq/gstreamer_via_jack.html) 
[2] [http://vhampiholi.blogspot.co.uk/2011/05/using-jack-for-gstreamer.html](http://vhampiholi.blogspot.co.uk/2011/05/using-jack-for-gstreamer.html)

---

### Post by kostkon on 2017-11-10
It's dconf nowadays, so you could check in there, using the... dconf-editor instead.

---

### Post by kazakore on 2017-11-11
> **kostkon said:**
> It's dconf nowadays, so you could check in there, using the... dconf-editor instead.

Installed and it does seem to have quite a lot more content that gconf-editor but still can't find anything relating to gstreamer, even using the find option....

---

