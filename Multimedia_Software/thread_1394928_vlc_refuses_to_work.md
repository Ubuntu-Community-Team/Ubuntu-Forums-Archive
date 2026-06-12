---
title: "vlc refuses to work"
date: 2010-01-31
forum: Multimedia Software
---

### Post by ottosykora on 2010-01-31
I have tried to install vlc on my ubuntu 9.04.
Initially all went fien, vlc was here and did work.
I tiried to uniinstall, then install again, still no cure. Any idea what went here wrong? And how to correct all?

next time I tried to run it, nothing happened, no process of vlc could be found and so I tried to start it form cmd with following results:

```







(<unknown>:5056): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(<unknown>:5056): Pango-CRITICAL **: pango_context_set_font_description: assertion `context != NULL' failed

(<unknown>:5056): Pango-CRITICAL **: pango_context_set_base_dir: assertion `context != NULL' failed

(<unknown>:5056): Pango-CRITICAL **: pango_context_set_language: assertion `context != NULL' failed

(<unknown>:5056): Pango-CRITICAL **: pango_layout_new: assertion `context != NULL' failed

(<unknown>:5056): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(<unknown>:5056): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(<unknown>:5056): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(<unknown>:5056): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(<unknown>:5056): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:5056): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:5056): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_screen_get_default_colormap: assertion `GDK_IS_SCREEN (screen)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_colormap_get_visual: assertion `GDK_IS_COLORMAP (colormap)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_screen_get_default_colormap: assertion `GDK_IS_SCREEN (screen)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed

(<unknown>:5056): Gdk-CRITICAL **: _gdk_window_new: assertion `GDK_IS_WINDOW (parent)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_new: assertion `window != NULL' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_enable_synchronized_configure: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_set_user_data: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_style_attach: assertion `window != NULL' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_style_set_background: assertion `GTK_IS_STYLE (style)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_paint_flat_box: assertion `GTK_IS_STYLE (style)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_set_accept_focus: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_set_focus_on_map: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_set_modal_hint: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_window_realize_icon: assertion `widget->window != NULL' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_screen_get_default_colormap: assertion `GDK_IS_SCREEN (screen)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_colormap_get_visual: assertion `GDK_IS_COLORMAP (colormap)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_screen_get_default_colormap: assertion `GDK_IS_SCREEN (screen)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed

(<unknown>:5056): Gdk-CRITICAL **: _gdk_window_new: assertion `GDK_IS_WINDOW (parent)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_new: assertion `window != NULL' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_set_user_data: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed

(<unknown>:5056): Gdk-CRITICAL **: _gdk_window_new: assertion `GDK_IS_WINDOW (parent)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_new: assertion `window != NULL' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_set_user_data: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed

(<unknown>:5056): Gdk-CRITICAL **: _gdk_window_new: assertion `GDK_IS_WINDOW (parent)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_new: assertion `window != NULL' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_set_user_data: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_style_attach: assertion `window != NULL' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_style_set_background: assertion `GTK_IS_STYLE (style)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_style_set_background: assertion `GTK_IS_STYLE (style)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_style_set_background: assertion `GTK_IS_STYLE (style)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_show: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_show: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed

(<unknown>:5056): Gdk-CRITICAL **: _gdk_window_new: assertion `GDK_IS_WINDOW (parent)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_new: assertion `window != NULL' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_set_user_data: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_style_attach: assertion `window != NULL' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_get_position: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_get_position: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_invalidate_maybe_recurse: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed

(<unknown>:5056): Gdk-CRITICAL **: _gdk_window_new: assertion `GDK_IS_WINDOW (parent)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_new: assertion `window != NULL' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_set_user_data: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_style_attach: assertion `window != NULL' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_get_position: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_get_position: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_invalidate_maybe_recurse: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed

(<unknown>:5056): Gdk-CRITICAL **: _gdk_window_new: assertion `GDK_IS_WINDOW (parent)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_new: assertion `window != NULL' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_set_user_data: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_style_attach: assertion `window != NULL' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_get_position: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_get_position: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gdk-CRITICAL **: gdk_window_invalidate_maybe_recurse: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:5056): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed


```

---

### Post by ottosykora on 2010-01-31
BTW, I tried also to autoclean and autoramove, but it did not helf either. I am still getting long list of errors when starting vlc.

Any idea what else I should uninstall or install in order to get vlc working?

---

