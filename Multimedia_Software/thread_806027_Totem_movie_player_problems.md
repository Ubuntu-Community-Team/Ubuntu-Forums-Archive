---
title: "Totem movie player problems"
date: 2008-05-24
forum: Multimedia Software
---

### Post by marc61 on 2008-05-24
I have a little problem with Totem. When I open an mpg video in Mozilla, the video immediately opens without any problems. 

When I try to open a wmv, a popup comes up asking me how I want to open the file and to browse for it. 

I don't get this. I have all the gstreamer plugins.

If Totem is the default player, why is it not acting that way?

---

### Post by kostkon on 2008-05-29
You have to add the package with *Windows* codecs, named *w32codecs*, that is offered by the [*Medibuntu* repository]("http://medibuntu.org/").

Thus, add this repository to your software sources list and then install the *w32codecs* and *gstreamer0.10-pitfdll* packages.

---

