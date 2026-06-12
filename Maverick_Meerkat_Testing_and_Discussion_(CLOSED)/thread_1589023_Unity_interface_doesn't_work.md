---
title: "Unity interface doesn't work?"
date: 2010-10-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by johnl on 2010-10-05
I thought I'd give the Unity interface a try on my laptop, which has an ATI Radeon X1300 with the open source radeon driver.

After selecting Unity from the gdm screen, I got the screen attached.

There's like a blue 'smudge' where the UI should be, and hovering over it results in a white box with a gray border.  

Whenever I do something that opens a new window, the UI flashes for a second (i.e. I can see the expected interface) and then disappears.

Any suggestions or advice on how to debug this?

---

### Post by kerry_s on 2010-10-05
you have composting enabled, only 1 can run at a time, the netbook ui uses mutter a composting wm.

turn off compiz & then try.

---

### Post by johnl on 2010-10-05
Hi,

that sounds like good advice, but compiz is not running.

```

$ ps aux | grep compiz
ledbettj 17687  0.0  0.0   4012   752 pts/0    S+   21:25   0:00 grep --color=auto compiz

```

When I launch "gnome-appearance-properties" and checked the Visual Effects tab, it's set to "None" and say "Mutter is running, can't switch to other effects."

Any other suggestions?

---

### Post by cariboo on 2010-10-05
Can your system do 3D in a normal desktop?

When mutter is running no other effects will work. 

Looking at your screenshot it looks like you are still in gnome-desktop.

---

### Post by johnl on 2010-10-05
The system can do 3d, yes.  My normal gnome-desktop session runs with compositing enabled.

I logged out, and at GDM when logging in selected "Ubuntu Netbook Edition."  If I'm supposed to do something else let me know.

AWN is set to run on login, so that's why that's there.

---

### Post by kerry_s on 2010-10-05
when you launch 1 of those programs from awn, does it have window decorations?

in 1 of those terminals:
[B]export CLUTTER_VBLANK=none
mutter --replace[/B]

---

### Post by johnl on 2010-10-05
> **kerry_s said:**
> when you launch 1 of those programs from awn, does it have window decorations?


no, the program runs maximized without window decorations, like you would expect it to under Unity, except the Unity part isn't there :)

> 
in 1 of those terminals:
[B]export CLUTTER_VBLANK=none
mutter --replace[/B]

the screen flickered while mutter restarted, but other than that no change.

Edit: OK, actually looks like the following might be the cause:

> 

(process:3793): mutter-WARNING **: 1

(process:3793): mutter-WARNING **: 3

(process:3793): mutter-WARNING **: 5

(process:3793): mutter-WARNING **: 4
(process:3793): mutter-DEBUG: OpenGL renderer string: Mesa DRI R300 (RS690 791F) 20090101 x86/MMX+/3DNow!+/SSE2 NO-TCL DRI2

** (mutter:3793): DEBUG: OpenGL renderer string: Mesa DRI R300 (RS690 791F) 20090101 x86/MMX+/3DNow!+/SSE2 NO-TCL DRI2

Window manager warning: Log level 16: Unable to find the file menu stock item

(mutter:3793): LIBDBUSMENU-GLIB-WARNING **: Unable to get property proxy for org.ayatana.indicator.session on /org/ayatana/indicator/session/menu: Could not get owner of name 'org.ayatana.indicator.session': no such name
(mutter:3793): Indicator-Sound-DEBUG: At start-up attempting to set the image to audio-volume-muted-panel
Window manager warning: Log level 128: Evaluating bitmask for '%l:%M %p'
Window manager warning: Log level 128: Checking against 2 posible times
Window manager warning: Log level 128: Guessing max time width: 58
Window manager warning: Log level 16: invalid (NULL) pointer instance
Window manager warning: Log level 8: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Window manager warning: Log level 16: invalid (NULL) pointer instance
Window manager warning: Log level 8: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Window manager warning: Log level 16: invalid (NULL) pointer instance
Window manager warning: Log level 8: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
(mutter:3793): libunity-private-DEBUG: unity_gesture_xcb_dispatcher_glue_init

(mutter:3793): LIBDBUSMENU-GLIB-CRITICAL **: id_prop_update: assertion `priv->root != NULL' failed

(mutter:3793): LIBDBUSMENU-GLIB-CRITICAL **: id_prop_update: assertion `priv->root != NULL' failed

(mutter:3793): LIBDBUSMENU-GLIB-CRITICAL **: id_prop_update: assertion `priv->root != NULL' failed
Window manager warning: Log level 16: invalid cast from `BamfApplication' to `BamfWindow'
Window manager warning: Log level 8: bamf_window_get_window_type: assertion `BAMF_IS_WINDOW (self)' failed
(mutter:3793): Indicator-Application-DEBUG: Connected to Application Indicator Service.
(mutter:3793): Indicator-Application-DEBUG: Setup proxy signals
(mutter:3793): Indicator-Application-DEBUG: Connect to them.
(mutter:3793): Indicator-Application-DEBUG: Request current apps
(mutter:3793): Indicator-Sound-DEBUG: about to connect to the signals
(mutter:3793): Indicator-Sound-DEBUG: indicator-sound: new_volume_slider_widget
(mutter:3793): Indicator-Sound-DEBUG: VolumeWidget::volume_widget_init
(mutter:3793): Indicator-Sound-DEBUG: volume_widget_set_twin_item initial level = 94.406128
(mutter:3793): Indicator-Sound-DEBUG: volume_widget_parent_changed
(mutter:3793): Indicator-Sound-DEBUG: indicator-sound: new_title_widget
(mutter:3793): Indicator-Sound-DEBUG: new_title_widget ("Rhythmbox")
(mutter:3793): Indicator-Sound-DEBUG: TitleWidget::title_widget_init
(mutter:3793): Indicator-Sound-DEBUG: indicator-sound: new_metadata_widget
(mutter:3793): Indicator-Sound-DEBUG: MetadataWidget::metadata_widget_init
(mutter:3793): Indicator-Sound-DEBUG: Metadata::At startup and image path = 
(mutter:3793): Indicator-Sound-DEBUG: indicator-sound: new_transport_bar() called 
(mutter:3793): Indicator-Sound-DEBUG: TransportWidget::transport_widget_init
Window manager warning: Log level 128: entry hint: Post message...
Window manager warning: Log level 128: entry_maybe_show_hint, nothing in the entry or not focused, so setting the hint to: Post message...
Window manager warning: Log level 16: /build/buildd/glib2.0-2.26.0/gobject/gsignal.c:2275: signal `destroy' is invalid for instance `0xa1a5ec0'
Window manager warning: Log level 128: Updating username label
Window manager warning: Log level 128: Using user icon for 'Guest Session' from file: (null)
Window manager warning: Log level 128: Username width 48px
Window manager warning: Log level 128: Font size 9.000000 pt
Window manager warning: Log level 128: Screen DPI 96.000000
Window manager warning: Log level 128: Username width 4.000000em
Window manager warning: Log level 128: new_application_item ("Set Up Chat...")
Window manager warning: Log level 128: new_application_item ("Set Up Mail...")
Window manager warning: Log level 128: new_application_item ("Broadcast")
Window manager warning: Log level 128: new_application_item ("Pidgin Internet Messenger")

[B](mutter:3793): Clutk-WARNING **: [CheckGLError] GL_INVALID_VALUE error in File ./ctk-render-target.c at line: 286

(mutter:3793): Clutk-WARNING **: [CheckGLError] OpenGL Error 1281 in File ./ctk-render-target.c at line: 286 


(mutter:3793): Clutk-WARNING **: Incomplete render target: 36057

(mutter:3793): Clutk-WARNING **: Incomplete render target: 36057

(mutter:3793): Clutk-WARNING **: [CheckGLError] UNKNOWN ERROR in File ./ctk-effect-cache.c at line: 298

(mutter:3793): Clutk-WARNING **: [CheckGLError] OpenGL Error 1286 in File ./ctk-effect-cache.c at line: 298 


(mutter:3793): Clutk-WARNING **: [CheckGLError] GL_INVALID_VALUE error in File ./ctk-render-target.c at line: 286

(mutter:3793): Clutk-WARNING **: [CheckGLError] OpenGL Error 1281 in File ./ctk-render-target.c at line: 286 
[/B]
(repeated x1000)


---

### Post by kerry_s on 2010-10-05
i seen a bug with similar output.
[https://bugs.launchpad.net/unity/+bug/593380](https://bugs.launchpad.net/unity/+bug/593380)

doesn't look like they have a fix yet

---

### Post by johnl on 2010-10-05
Yup, that looks like it -- thanks for tracking that down.  Bummer.

---

