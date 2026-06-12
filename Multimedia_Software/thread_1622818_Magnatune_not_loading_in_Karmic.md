---
title: "Magnatune not loading in Karmic"
date: 2010-11-15
forum: Multimedia Software
---

### Post by frogotronic on 2010-11-15
Hi,

  Can not load magnatune in rhythmbox -> constant "loading" and nothing happens.

Here's the terminal output:

```
$ rhythmbox

** (rhythmbox:16630): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:16630): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/magnatune/MagnatuneSource.py", line 139, in do_impl_activate
    self.__move_data_files()
  File "/usr/lib/rhythmbox/plugins/magnatune/MagnatuneSource.py", line 572, in __move_data_files
    magnatune_in_progress_dir = magnatune_in_progress_dir.get_path()
UnboundLocalError: local variable 'magnatune_in_progress_dir' referenced before assignment

** (rhythmbox:16630): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:16630): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:16630): CRITICAL **: murrine_style_draw_box: assertion `height >= -1' failed
```

- CH

---

