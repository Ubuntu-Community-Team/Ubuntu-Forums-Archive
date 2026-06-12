---
title: "Rhythmbox not starting Ubuntu 10.10."
date: 2010-12-23
forum: Multimedia Software
---

### Post by haircat on 2010-12-23
Rhythmbox not starting Ubuntu 10.10.

It was installed several times{uninstalled then reinstalled}

It just will not start.

haircat

---

### Post by sikander3786 on 2010-12-23
Applications > Accessories > Terminal, type this,

```
rhythmbox
```

Copy/paste the error message here.

---

### Post by haircat on 2010-12-23
(rhythmbox:13903): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)

Thanks for the help terminal started rhythmbox

haircat

---

### Post by sikander3786 on 2010-12-23
> terminal started rhythmbox

Are you also able to start it from Appications menu?

Make sure there aren't any broken packages. From Terminal,

```
sudo apt-get update
```

```
sudo dpkg --configure -a
```

---

