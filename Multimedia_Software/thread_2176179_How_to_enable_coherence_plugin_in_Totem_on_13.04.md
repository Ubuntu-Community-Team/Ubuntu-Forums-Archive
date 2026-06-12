---
title: "How to enable coherence plugin in Totem on 13.04?"
date: 2013-09-23
forum: Multimedia Software
---

### Post by andy.stevens on 2013-09-23
Hi,

Does the coherence plugin for Totem work in 13.04?  I've read the instructions on [http://coherence.beebits.net/wiki/Totem](http://coherence.beebits.net/wiki/Totem) but haven't got it working.
I've installed the python-coherence package via the Software Centre, which has created the /usr/share/dbus-1/services/org.Coherence.service file mentioned in the wiki page.  I've downloaded the upnp-coherence.py  & upnp-coherence.totem-plugin files from [http://coherence.beebits.net/browser/trunk/Coherence/misc/Totem-Plugin](http://coherence.beebits.net/browser/trunk/Coherence/misc/Totem-Plugin) into ~/.local/share/totem/plugins/ as mentioned on the wiki page (since the Totem version is >=2.22) and the org/gnome/Totem/disable-user-plugins key is false in dconf Editor.  But when I run Totem and go to Edit -> Plugins to enable it, there's no sign of it in the list.

Guided by the instructions on 
[https://developer.gnome.org/totem/unstable/totem-plugins.html](https://developer.gnome.org/totem/unstable/totem-plugins.html), I've also tried putting the files in a ~/.local/share/totem/plugins/upnp-coherence directory, renaming .totem-plugin file to just .plugin and editing it to use "[Plugin]" on the first line instead of "[Totem Plugin]".  That got it to show up in the Edit -> Plugins list, at least, but when I click the checkbox to enable it Totem just freezes up then vanishes; running from the command line I see that it outputs
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:40: Warning: specified class size for type `PyGtkGenericCellRenderer' is smaller than the parent type's `GtkCellRenderer' class size
  from gtk import _gtk
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:40: Warning: g_type_get_qdata: assertion `node != NULL' failed
  from gtk import _gtk
Segmentation fault (core dumped)

Is it possible to get this plugin working in Totem on Ubuntu 13.04?  Alternatively, is there some other UPnP client plugin I can use to watch videos in Totem via DNLA from my Humax PVR?  Or is VNC my only option?


Andy.

---

### Post by Justin_Frahm on 2014-02-02
I'm really dissappointed to see that nobody has anything helpful to say here; I'm having the exact same problem.

Anybody out there who knows something?

---

### Post by yamameguy on 2014-05-10
Sorry I'm of no help other than to share your misery, but it does the exact same thing in 14.04 :(

---

### Post by yamameguy on 2014-05-10
Good news! I don't have a fix, but I did find a workaround:

[http://askubuntu.com/questions/88754/upnp-dlna-client-player-recommendations](http://askubuntu.com/questions/88754/upnp-dlna-client-player-recommendations)

Go down to the answer that discusses using djmount. It's not perfect (every "view" that Plex can deliver winds up listed as a folder and the All folder has to be chosen) but it allows me to use either Totem or VLC. Thumbnail description: it uses fuse and djmount to create a local mount of the upnp files. From there, totem or vlc are good to go.

---

