---
title: "Rhythmbox spontaneous closing down issue."
date: 2010-11-28
forum: Multimedia Software
---

### Post by rich52x on 2010-11-28
I do enjoy using Rhythmbox, but one thing that's getting at me, and may lead me to switch media players, is that every now and again (It happens at least once a day) I go to change the volume of the music, and while sliding the volume controller, it will just spontaneously shut down, and I'll have to start the program again. It's not the end of the world, but it's pretty damn annoying, any ideas? Thanks in advance

Rich.

---

### Post by Yellow Pasque on 2010-11-28
Probably a segfault. Start rhythmbox from the terminal and post the output. Bonus points if you install rhythmbox-dbg, and actually obtain a backtrace that a dev can follow. Star stickers if you actually file a bug report on launchpad (or add info to an existing one).
```
sudo apt-get install rhythmbox-dbg apport-gtk
```

---

### Post by rich52x on 2010-11-29
Okay, I opened rhythmbox from the terminal, receiving the output,
```
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:77: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:77: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:78: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:93: Murrine configuration option "style" is no longer supported and will be ignored.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:172: Murrine configuration option "style" is no longer supported and will be ignored.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:202: Murrine configuration option "style" is no longer supported and will be ignored.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:310: Murrine configuration option "style" is no longer supported and will be ignored.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:344: Murrine configuration option "style" is no longer supported and will be ignored.
** (rhythmbox:7396): DEBUG: Loading the real store page
** (rhythmbox:7396): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token
** (rhythmbox:7396): DEBUG: navigation requested to http://stores.7digital.com/default.aspx?shop=34&partner=983

```

I then installed rhythmmbox-dbg, and decided to run rhythmbox again from the terminal, receiving the output:
```
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:77: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:77: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:78: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:93: Murrine configuration option "style" is no longer supported and will be ignored.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:172: Murrine configuration option "style" is no longer supported and will be ignored.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:202: Murrine configuration option "style" is no longer supported and will be ignored.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:310: Murrine configuration option "style" is no longer supported and will be ignored.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:344: Murrine configuration option "style" is no longer supported and will be ignored.
** (rhythmbox:7490): DEBUG: Loading the real store page
** (rhythmbox:7490): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token

(rhythmbox:7490): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:7490): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:7490): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:7490): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:7490): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:7490): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:7490): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:7490): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:7490): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed
** (rhythmbox:7490): DEBUG: navigation requested to http://stores.7digital.com/default.aspx?shop=34&partner=983

```

Unfortunately, being the semi-newbie I am, I don't actually know how to obtain a backtrace, would you be able to explain it to me? BTW, I'm in the process of filing a bug report on launchpad, so just bear with me on that one. Thanks again

Rich.

---

### Post by Yellow Pasque on 2010-11-29
Well, it doesn't appear to be segfaulting. Try disabling the Ubuntu Music store plugin unles you need it, as that's known to cause problems.

---

### Post by rich52x on 2010-11-29
Okay I've disabled the Ubuntu Music Store plugin, I don't really use it much anyway, so no biggie, I'll get back if it makes a difference or not in a bit. Thanks again :)

Rich.

---

