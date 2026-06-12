---
title: "gstreamer problem, totem fails to launch"
date: 2009-03-22
forum: Multimedia Software
---

### Post by AndyBoy_LV on 2009-03-22
I`ve been trying to install subtitleeditor, and he asked me to install gstreamer and it`s plugins. so i installed them, but after compiling and install subtitleeditor, it couldn`t lunch any files, saying that it is gstreamer`s plugin`s problem. So i decided to reinstall them, and after reinstall i cannot launch Totem and Decibel Audio Player any more. Totem says:

```

** (totem:8856): DEBUG: Init of Python module
** (totem:8856): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:8856): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:8856): DEBUG: Creating Python plugin instance

** (totem:8856): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
** (totem:8856): DEBUG: Init of Python module
totem: symbol lookup error: /usr/lib/python2.5/site-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_control_source_get_type

```

and Decibel says:
```

python: symbol lookup error: /usr/lib/python2.5/site-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_control_source_get_type

```

Any help would be appreciated.

P.S. i`m not sure if something else doesn`t work too. I know that VLC still plays movies.

---

### Post by Mister_Joshua on 2009-03-22
I ran into this while trying to get 8.10 set up last night.  My solution was to go into Synaptic and get every plugin I could find for gstreamer.  That may have been dumb but it got Totem working.

Good luck!

---

### Post by AndyBoy_LV on 2009-03-22
> **Mister_Joshua said:**
> I ran into this while trying to get 8.10 set up last night.  My solution was to go into Synaptic and get every plugin I could find for gstreamer.  That may have been dumb but it got Totem working.

Good luck!

Thanks for the answer! But that`s what i did already, but it just doesn`t help :((

---

### Post by AndyBoy_LV on 2009-03-22
A little update:

I have been able to run Totem.  I deleted
 ```
sudo rm /usr/lib/python2.5/site-packages/gst-0.10/gst/_gst.so
```
and than launched Totem. It said about error, but after i unchecked Youtube plugin it now runs good. I was also able to launch Decibel-audio-player, but it couldn`t play any music.

i later reinstalled python-gst0.10 and Totem still runs good. However decibel now gives me the old error:

```
python: symbol lookup error: /usr/lib/python2.5/site-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_control_source_get_type

```

---

