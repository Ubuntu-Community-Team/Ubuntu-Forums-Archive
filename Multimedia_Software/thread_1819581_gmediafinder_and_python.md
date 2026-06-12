---
title: "gmediafinder and python"
date: 2011-08-06
forum: Multimedia Software
---

### Post by oliv66 on 2011-08-06
Hi all,

gmediafinder does not work any more beacause of python.

```
gmediafinder 
Xlib.protocol.request.QueryExtension
Traceback (most recent call last):
  File "/usr/bin/gmediafinder", line 23, in <module>
    app = gmediafinder.GsongFinder()
  File "/usr/lib/pymodules/python2.7/GmediaFinder/gmediafinder.py", line 334, in __init__
    self.load_gui_icons()
  File "/usr/lib/pymodules/python2.7/GmediaFinder/gmediafinder.py", line 811, in load_gui_icons
    pb = gtk.gdk.pixbuf_new_from_file(img_path+"/paypal.gif")
glib.GError: Failed to open file '/usr/share/gmediafinder/img/paypal.gif': No such file or directory

```

I don't know how to fix it?

Help is welcome,

Regards,

Olivier

---

### Post by smo on 2011-08-07
hi

i m the gmf dev...

just update from ppa or git ...

++

---

### Post by oliv66 on 2011-08-07
Hi,

yes it works after updating....

I was about to publish it.

Regards,

Olivier

---

