---
title: "Rythmbox keeps crashing"
date: 2013-03-04
forum: Multimedia Software
---

### Post by samsom63 on 2013-03-04
Rythmbox has become unusable as of late as it keeps crashing when I try to launch it. It worked well initially, and the problem appeared about a week ago. If I try to launch the programme several times, it eventually starts but not for long.

Any idea what may cause the problem? it's annoying because i like rythmbox, and because I enjoy the radio lens which also use rythmbox. I dont have any problem with Musique.

---

### Post by stinkeye on 2013-03-04
Start rhythmbox in the terminal to see any errors.
May be caused by a plugin.
Note the spelling...```
rhythmbox
```

---

### Post by samsom63 on 2013-03-04
> **stinkeye said:**
> Start rhythmbox in the terminal to see any errors.
May be caused by a plugin.
Note the spelling...```
rhythmbox
```

Of course, now it works :-D It loaded my library properly but still got this string of errors:
```

(rhythmbox:15550): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/ubuntuone/MusicStoreWidget.py", line 105, in url_loaded
    if parseurl(url)[2] == "https":
  File "/usr/lib/python2.7/urlparse.py", line 140, in urlparse
    tuple = urlsplit(url, scheme, allow_fragments)
  File "/usr/lib/python2.7/urlparse.py", line 179, in urlsplit
    i = url.find(':')
AttributeError: 'NoneType' object has no attribute 'find'


(rhythmbox:15550): Gtk-CRITICAL **: gtk_tree_model_get_iter_first: assertion `GTK_IS_TREE_MODEL (tree_model)' failed


(rhythmbox:15550): Gtk-CRITICAL **: gtk_combo_box_set_active_iter: assertion `GTK_IS_COMBO_BOX (combo_box)' failed


(rhythmbox:15550): Gtk-CRITICAL **: gtk_list_store_clear: assertion `GTK_IS_LIST_STORE (list_store)' failed


(rhythmbox:15550): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed


(rhythmbox:15550): Gtk-CRITICAL **: gtk_combo_box_set_active: assertion `GTK_IS_COMBO_BOX (combo_box)' failed


(rhythmbox:15550): Gtk-CRITICAL **: gtk_label_set_markup: assertion `GTK_IS_LABEL (label)' failed


(rhythmbox:15550): Gtk-CRITICAL **: gtk_label_set_markup: assertion `GTK_IS_LABEL (label)' failed

```

---

