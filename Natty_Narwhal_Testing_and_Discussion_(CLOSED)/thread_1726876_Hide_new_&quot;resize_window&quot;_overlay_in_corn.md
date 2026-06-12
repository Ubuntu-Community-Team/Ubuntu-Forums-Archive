---
title: "Hide new &quot;resize window&quot; overlay in corner of windows?"
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by bretthoerner on 2011-04-11
Is there a way to hide or disable this annoying new icon in the bottom right corner of every window?

---

### Post by bretthoerner on 2011-04-12
Bump.

---

### Post by lucazade on 2011-04-12
No, You can't without recompiling all gtk+ stack.. unfortunately :/

---

### Post by rajeev1204 on 2011-04-12
> **bretthoerner said:**
> Is there a way to hide or disable this annoying new icon in the bottom right corner of every window?

What theme are you using? new wave?

---

### Post by bretthoerner on 2011-04-12
> **lucazade said:**
> No, You can't without recompiling all gtk+ stack.. unfortunately :/

The whole stack? Is it not just something enabled in one package? I'm happy to rebuild a .deb for myself --- can you point out which package it's in and/or what the resize thing is called?

It's super distracting and covers up the actual UI in some apps. Annoying, annoying, annoying. :(

---

### Post by mc4man on 2011-04-12
> **bretthoerner said:**
> The whole stack? Is it not just something enabled in one package? I'm happy to rebuild a .deb for myself --- can you point out which package it's in and/or what the resize thing is called?

It's super distracting and covers up the actual UI in some apps. Annoying, annoying, annoying. :(

You have to rebuild the gtk+2.0 source. If you do it as a package build (preferred ) then you'll only need to replace 1 of the .deb's created (libgtk2.0-0 ...
The build is easy, it just requires a fair amount of deps (200+MB) and takes awhile.

i use ambiance where the only time it was much of an annoyance was with the terminal w/ no scrollbars, that has since been made better w/ an update to light-themes so hardly worth the effort

Edit: IIRC correctly I didn't even bother with removing the resize_grip, just changed it's size to 1x1 which makes it pretty much invisible

---

### Post by bretthoerner on 2011-04-12
> **mc4man said:**
> Edit: IIRC correctly I didn't even bother with removing the resize_grip, just changed it's size to 1x1 which makes it pretty much invisible

Are you able to do this without a recompile?

I'm fine with unpatching the deb, I'm going to do that now. I run Xmonad as a window manager inside of Gnome, so I'm probably a special case. The corners are really, really annoying to me.

Thanks for your help.

---

### Post by mc4man on 2011-04-12
> Are you able to do this without a recompile?
No, it's in the patch - currently 16x16
```
@@ -816,6 +874,21 @@
 							1.0,
 							@@ -816,6 +874,21 @@
 							1.0,
 							GTK_PARAM_READWRITE));
 
+  /* Style properties.
+   */
+    gtk_widget_class_install_style_property (widget_class,
+                                             g_param_spec_int ("resize-grip-width",
+                                                               P_("Width of resize grip"),
+                                                               P_("Width of resize grip"),
+                                                               0, G_MAXINT, 16, GTK_PARAM_READWRITE));
+
+    gtk_widget_class_install_style_property (widget_class,
+                                             g_param_spec_int ("resize-grip-height",
+                                                               P_("Height of resize grip"),
+                                                               P_("Height of resize grip"),
+                                                               0, G_MAXINT, 16, GTK_PARAM_READWRITE));
+

```

This post shows ex. w/ the 1x1 grip area
[http://ubuntuforums.org/showthread.php?p=10616979#post10616979](http://ubuntuforums.org/showthread.php?p=10616979#post10616979)

---

### Post by chrisccoulson on 2011-04-12
> **mc4man said:**
> No, it's in the patch - currently 16x16
```
@@ -816,6 +874,21 @@
 							1.0,
 							@@ -816,6 +874,21 @@
 							1.0,
 							GTK_PARAM_READWRITE));
 
+  /* Style properties.
+   */
+    gtk_widget_class_install_style_property (widget_class,
+                                             g_param_spec_int ("resize-grip-width",
+                                                               P_("Width of resize grip"),
+                                                               P_("Width of resize grip"),
+                                                               0, G_MAXINT, 16, GTK_PARAM_READWRITE));
+
+    gtk_widget_class_install_style_property (widget_class,
+                                             g_param_spec_int ("resize-grip-height",
+                                                               P_("Height of resize grip"),
+                                                               P_("Height of resize grip"),
+                                                               0, G_MAXINT, 16, GTK_PARAM_READWRITE));
+

```
If you re-build without the patch then you'll need to adjust gtk+-2.24.4/debian/libgtk2.0-0.symbols, I believe there are about 8 ref.'s to resize_grip, but I only found 4 to be removed.
(could attach file if need be

This post shows ex. w/ the 1x1 grip area
[http://ubuntuforums.org/showthread.php?p=10616979#post10616979](http://ubuntuforums.org/showthread.php?p=10616979#post10616979)

Well, the "16" is only the default. The value is themeable though (hence why it is exposed like this).

Just add this to the default style in the gtkrc for your theme:

```
GtkWindow::resize-grip-width = 1
GtkWindow::resize-grip-height = 1
```

No need to recompile anything ;)

---

### Post by mc4man on 2011-04-12
> Well, the "16" is only the default. The value is themeable though (hence why it is exposed like this)

Is it then editable in the theme? (see your edit, much better..

bretthoerner - The reason behind resizing was I decided it was a rather poor idea to mess with the gtk source itself, other than changing 2 values

---

### Post by kendon on 2011-04-14
> **chrisccoulson said:**
> Well, the "16" is only the default. The value is themeable though (hence why it is exposed like this).

Just add this to the default style in the gtkrc for your theme:

```
GtkWindow::resize-grip-width = 1
GtkWindow::resize-grip-height = 1
```

No need to recompile anything ;)

this works perfectly, thank you very much for the hint. i can't express how little i could be arsed to recompile anything for this, let alone doing it on a regular basis.

---

### Post by chrisccoulson on 2011-04-14
> **kendon said:**
> this works perfectly, thank you very much for the hint. 

You're welcome :)

---

