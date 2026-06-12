---
title: "(gedit:2152): GLib-GObject-CRITICAL"
date: 2010-10-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by karmila on 2010-10-08
I don't know if this is specific maverick related but because I'm using Maverick I decided to post it here. :)
The problem is each time I open gedit window from terminal and then close it I always get this warning "**(gedit:2152): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed**"
Here is the sample:
> strider@strider-desktop:~$ gksu gedit /etc/default/apport

(gedit:2152): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(gedit:2152): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed
strider@strider-desktop:~$ gksu gedit /etc/default/burg

(gedit:2171): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(gedit:2171): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(gedit:2171): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failedI have no clue what this is mean :confused:

---

