---
title: "To access inner functionalities from C++ program or scripts"
date: 2012-04-14
forum: Multimedia Software
---

### Post by srijith141 on 2012-04-14
hi,
   I wanted an image viewer application which i could use in my desktop application to display image and change the image without using buttons provided in the image viewer or the keyboard.
Is this really possible to do or not??? 

    If this functionality can't be provided in EOG then please tell which particular application can be used...

thanks,

regards,
srijith

---

### Post by enkay009 on 2012-04-14
I hope I understood you correctly. You want to embed an image viewer in an application you're building?

If so, have a look at this tutorial on the GTK3 dev site: [http://developer.gnome.org/gnome-devel-demos/unstable/image-viewer.cpp.html.en](http://developer.gnome.org/gnome-devel-demos/unstable/image-viewer.cpp.html.en)

To summarize there is a class called GTK::Image that you can use for this. And this library has C++ bindings.

---

