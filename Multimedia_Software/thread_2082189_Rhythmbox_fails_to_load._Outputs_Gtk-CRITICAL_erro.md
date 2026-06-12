---
title: "Rhythmbox fails to load. Outputs Gtk-CRITICAL error message."
date: 2012-11-08
forum: Multimedia Software
---

### Post by /bee/ on 2012-11-08
I'm at a loss here.  I had rhythmbox working just fine and then I installed several updates today and restarted my machine.  Now, the Rhythmbox window loads and immediately becomes unresponsive -- before loading my library.  When run through Terminal, I get the following:

v2.98 on 12.10 x64

```
(rhythmbox:5262): Gtk-CRITICAL **: gtk_tree_model_get_iter_first: assertion `GTK_IS_TREE_MODEL (tree_model)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_combo_box_set_active_iter: assertion `GTK_IS_COMBO_BOX (combo_box)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_list_store_clear: assertion `GTK_IS_LIST_STORE (list_store)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_combo_box_set_active: assertion `GTK_IS_COMBO_BOX (combo_box)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_label_set_markup: assertion `GTK_IS_LABEL (label)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_label_set_markup: assertion `GTK_IS_LABEL (label)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_tree_model_get_iter_first: assertion `GTK_IS_TREE_MODEL (tree_model)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_combo_box_set_active_iter: assertion `GTK_IS_COMBO_BOX (combo_box)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_list_store_clear: assertion `GTK_IS_LIST_STORE (list_store)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_combo_box_set_active: assertion `GTK_IS_COMBO_BOX (combo_box)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_label_set_markup: assertion `GTK_IS_LABEL (label)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_label_set_markup: assertion `GTK_IS_LABEL (label)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_tree_model_get_iter_first: assertion `GTK_IS_TREE_MODEL (tree_model)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_combo_box_set_active_iter: assertion `GTK_IS_COMBO_BOX (combo_box)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_list_store_clear: assertion `GTK_IS_LIST_STORE (list_store)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_combo_box_set_active: assertion `GTK_IS_COMBO_BOX (combo_box)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_label_set_markup: assertion `GTK_IS_LABEL (label)' failed

(rhythmbox:5262): Gtk-CRITICAL **: gtk_label_set_markup: assertion `GTK_IS_LABEL (label)' failed

```

---

