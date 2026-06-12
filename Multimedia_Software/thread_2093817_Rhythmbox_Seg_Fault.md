---
title: "Rhythmbox Seg Fault"
date: 2012-12-11
forum: Multimedia Software
---

### Post by intercept on 2012-12-11
When I start to play a track, Rhythmbox closes out with a seg fault.

Here is the CLI output. Please help!

```
adam@adam-desktop:~$ rhythmbox

** (rhythmbox:23095): WARNING **: GObject.get_data() and set_data() are deprecated. Use normal Python attributes instead

(rhythmbox:23095): Rhythmbox-WARNING **: Could not open device /dev/radio0

(rhythmbox:23095): Gtk-CRITICAL **: gtk_tree_model_get_iter_first: assertion `GTK_IS_TREE_MODEL (tree_model)' failed

(rhythmbox:23095): Gtk-CRITICAL **: gtk_combo_box_set_active_iter: assertion `GTK_IS_COMBO_BOX (combo_box)' failed

(rhythmbox:23095): Gtk-CRITICAL **: gtk_list_store_clear: assertion `GTK_IS_LIST_STORE (list_store)' failed

(rhythmbox:23095): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(rhythmbox:23095): Gtk-CRITICAL **: gtk_combo_box_set_active: assertion `GTK_IS_COMBO_BOX (combo_box)' failed

(rhythmbox:23095): Gtk-CRITICAL **: gtk_label_set_markup: assertion `GTK_IS_LABEL (label)' failed

(rhythmbox:23095): Gtk-CRITICAL **: gtk_label_set_markup: assertion `GTK_IS_LABEL (label)' failed

** (rhythmbox:23095): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/platform/ipc/linux.py", line 756, in get_info
    return self.service.folders.get_info(path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 166, in inner
    result = f(*new_args, **new_kwargs)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/logger.py", line 283, in inner
    res = f(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 721, in get_info
    mdobj = self.fs_manager.get_by_path(path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 795, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'


** (rhythmbox:23095): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

(rhythmbox:23095): RhythmDB-WARNING **: attempt to use same location in multiple entry types

(rhythmbox:23095): RhythmDB-WARNING **: attempt to use same location in multiple entry types

(rhythmbox:23095): RhythmDB-WARNING **: attempt to use same location in multiple entry types

(rhythmbox:23095): RhythmDB-WARNING **: attempt to use same location in multiple entry types

(rhythmbox:23095): RhythmDB-WARNING **: attempt to use same location in multiple entry types

(rhythmbox:23095): RhythmDB-WARNING **: attempt to use same location in multiple entry types

(rhythmbox:23095): GLib-GObject-CRITICAL **: g_value_get_uint64: assertion `G_VALUE_HOLDS_UINT64 (value)' failed

(rhythmbox:23095): GLib-GObject-CRITICAL **: g_value_get_uint64: assertion `G_VALUE_HOLDS_UINT64 (value)' failed
Segmentation fault (core dumped)

```

---

