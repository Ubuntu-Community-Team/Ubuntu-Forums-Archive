---
title: "GTK+3.0 is released"
date: 2011-02-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-02-12
Here is the announcement:
[http://mail.gnome.org/archives/gnome-announce-list/2011-February/msg00022.html](http://mail.gnome.org/archives/gnome-announce-list/2011-February/msg00022.html)

---

### Post by ratcheer on 2011-02-12
Thanks. I saw that yesterday and wondered why no one had mentioned it.

Tim

---

### Post by amano on 2011-02-12
I don't think that we will see much of it in Natty's Main. I think the big conversion will happen for 11.10.

---

### Post by Harry33 on 2011-02-12
> **amano said:**
> I don't think that we will see much of it in Natty's Main. I think the big conversion will happen for 11.10.

The GTK+3.0 packages are in the Natty already, just not the release version.
There is the version 2.99.3-0ubuntu1.
The release version will be there soon.

---

### Post by dext on 2011-02-12
GTK2.24 and GTK3.0.0 are compatible running alongside each other

---

### Post by Harry33 on 2011-02-12
> **dext said:**
> GTK2.24 and GTK3.0.0 are compatible running alongside each other

Yes they are. Actually it is GTK+2.0, the latest version being 2.24.0
But if they weren't, we would be in great trouble.
There will be quite a long time applications left, that depend on GTK+2.0.

---

### Post by xtoudi on 2011-02-12
I'm affraid that GTK+3 is not compatible with GTK+2 so this is why we need to have both of them now and in the "near?" future. This is true.

---

### Post by dext on 2011-02-12
> **xtoudi said:**
> I'm affraid that GTK+3 is not compatible with GTK+2 so this is why we need to have both of them now and in the "near?" future. This is true.

got anything to back that up? cause i know it is , search through Phoronix stories about it an you will see that it is,

---

### Post by bruce89 on 2011-02-12
> **xtoudi said:**
> I'm affraid that GTK+3 is not compatible with GTK+2 so this is why we need to have both of them now and in the "near?" future. This is true.

They are binary incompatible, but parallel installable. Means you can have 2.x and 3.x installed, and they won't interfere with each other (providing no application tries to use both at once).

---

### Post by Harry33 on 2011-02-13
> **bruce89 said:**
> They are binary incompatible, but parallel installable. Means you can have 2.x and 3.x installed, and they won't interfere with each other (providing no application tries to use both at once).

This is true.
You can test it by installing GTK+3.0 packages:
gir1.2-gtk-3.0, gtk3-engines-pixbuf, libgail3.0-0, libgtk3.0-0, libgtk3.0-bin, libgtk3.0-common.

You can also install and use both Gnome-shell (depends on GTK+3.0) and Unity (depends on GTK+2.0).

---

