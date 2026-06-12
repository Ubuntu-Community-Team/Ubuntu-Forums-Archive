---
title: "Additional Drivers aka jockey-gtk errors in 12.04LTS"
date: 2013-10-04
forum: Multimedia Software
---

### Post by Handssolow on 2013-10-04
In trying to get any AMD driver installed for a Radeon HD7950 card as jockey-gtk is broken with the following errors-

(jockey-gtk:2733): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed
Exception in thread thread_call_progress_dialog:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 551, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/threading.py", line 504, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply.
Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply
the reply timeout expired, or the network connection was broken.

Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 418, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 468, in run
    self.ui_show_main()
  File "/usr/bin/jockey-gtk", line 94, in ui_show_main
    self.update_tree_model()
  File "/usr/bin/jockey-gtk", line 274, in update_tree_model
    for h_id in self.get_displayed_handlers():
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 819, in get_displayed_handlers
    return self.backend().available(self.argv_options.mode)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply.
Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply,
the reply timeout expired, or the network connection was broken.

I've re-installed all things python and dbus to no effect. Obviously I've done many searches with no appropriate solution that I can find.
Originally I managed to get the 13.4 AMD Catalyst driver (version 29th May 2013) installed and working.
After I attempted to install the AMD experimental beta driver either manually through the terminal or via synaptic, I'm left with no GUI and have to purge fglrx to get one back.

Things don't seem to be helped by the lack of support for 12.04LTS as far as jockey-gtk is concerned. The caravan has moved on and Additional drivers are now handled differently in 12.10 and onwards.

Anyone with suggestions how I might recover jockey-gtk without yet another reinstall of 12.04LTS and be able to install the latest AMD video driver?

---

### Post by Handssolow on 2013-10-05
Searching yields several reports of people like me still experiencing errors with Additional Drivers/jockey-gtk despite launchpad comments that this had been fixed. No it hasn't.

Faced with a none working jockey-gtk, I had anther session at trying to install a working AMD driver on a 12.04LTS 64 bit desktop.  I was unsuccessful at manually installing the latest 13.10Beta2 with the terminal (having first downloaded the driver from the AMD website). I gave it two attempts, purging after each failed attempt.
Success was achieved using synaptic and choosing the three fglrx-experimental-13 packages ( fglrx-experimental-13,  fglrx-experimental-13-dev,  fglrx-amdcccle-experimental-13).

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7900 Series
OpenGL version string: 4.2.12337 Compatibility Profile Context 13.20.11

fgl_glxgears seems to work OK with none of the slowdown after 30 seconds I'd experienced with an earlier driver install.

So I'm relieved I've a working AMD driver for the Radeon HD 7950 graphics card but jockey-gtk is broken and needs fixing in 12.04LTS.

---

### Post by Handssolow on 2013-10-06
Only downside is that bootup now takes about 1.5 minutes. The faint purple screen is eventually replaced by the login screen. It's taught me that in future I shouldn't rush into assuming that the AMD fglrx driver hasn't installed and hit reset too soon.

So it's still work in progress to sort out the slow boot, perhaps bootchart and pybootchartgui will offer some pointers. At the moment my son is using the PC to play Oblivion ES, so that's progress.

I'll start a new thread if I make progress on the slow boot issue, if anyone has suggestions how to mend jockey-gtk on 12.04LTS please comment.

---

