---
title: "Rhythmbox now crashing after opening-Long"
date: 2012-12-29
forum: Multimedia Software
---

### Post by kodb on 2012-12-29
Good morning.
Last night I began experiencing Rhythmbox crashing when I open it.
I am running 12.04.1 and using RB 2.98 from webupd8 ppa.  I have googled this for hours and have tried disabling and deleting the magnatune plugin as well as purging the foss ppa for 3rd party plugins.  If I start RB from terminal using the  --disable plugin tag then I can run the thing but no plugins (we use the daap server at home for our entire house).
I went ahead and recorded the output from the CLI and it is below:
```

bob@LR:~$ rhythmbox

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

(rhythmbox:11675): libdmapsharing-WARNING **: Ignoring local service living room

(rhythmbox:11675): libdmapsharing-WARNING **: Ignoring local service living room
Segmentation fault (core dumped)


```

I am a bit clueless of where to go from here.  To recap steps taken already include:
deleting the magnatune folder in the plugins 
purging the ppas
purging and reinstalling RB completely
googling until my fingers cramped :)

Any help greatly appreciated

Bob

---

### Post by gnush on 2012-12-29
Can you run Rhythmbox with gdb and see exactly where it fails, and see if you can get some additional information?

Have you tried running it as root for shits and giggles? While it's doubtful it's a privilege problem, you never know until you try.

---

### Post by kodb on 2012-12-29
Gnush,
Tried as root but no joy.
Have not ever used gdb so I will google and try that
Thanks!
Bob

---

### Post by davidmohammed on 2013-01-01
I've seen this in the past.

Try using dconf-editor (install dconf-tools package)

then navigate to org.gnome.rhythmbox.plugins

click the "active-plugins" key and in the bottom right click "set to default".

Repeat this for the "seen plugins" key.

---

