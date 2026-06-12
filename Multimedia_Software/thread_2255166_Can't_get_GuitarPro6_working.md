---
title: "Can't get GuitarPro6 working"
date: 2014-12-02
forum: Multimedia Software
---

### Post by matthew45 on 2014-12-02
Hello!

I've got some trouble with installing GuitarPro6 on my Ubuntu based distro(Dreamstudio)

Few months ago I've installed it without any problems, but yesterday, it suddenly stopped working.
After reinstalling Dreamstudio, I tried to install Guitarpro6 like that:
1. I made modified .deb file and installed it like in this post(but didn't installed *ia32-libs*, because there are some problems with that):
[http://ubuntuforums.org/showthread.php?t=1458626&page=3&p=12106975#post12106975](http://ubuntuforums.org/showthread.php?t=1458626&page=3&p=12106975#post12106975)

There is a description of that problems with *ia32-libs*:

When I try to install *ia32-libs*, I get this:
```
The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unable to correct problems, you have held broken packages.
```
When I try to install *ia32-libs-multiarch*, I get this:
```
The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: libcanberra-gtk-module:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```
When I try to install *libcanberra-gtk-module:i386*, I get this:
```
The following packages have unmet dependencies:
 libcanberra-gtk-module:i386 : Depends: libcanberra-gtk0:i386 (>= 0.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Some packages later...

When I try to install *libtdb1:i386*, it can be done, but it would delete almost everything from my system! Here is the result from terminal:
```
The following packages will be REMOVED:
  agave aisleriot brasero brasero-cdrkit celtx dreamstudio-3d-design
  dreamstudio-artwork dreamstudio-audio-control dreamstudio-audio-effects
  dreamstudio-audio-essentials dreamstudio-audio-recording
  dreamstudio-audio-utilities dreamstudio-complete dreamstudio-desktop
  dreamstudio-dj-tools dreamstudio-graphic-design dreamstudio-greeter
  dreamstudio-instruments dreamstudio-photography dreamstudio-scoring
  dreamstudio-video gir1.2-rb-3.0 gnome-alsamixer gnome-control-center
  gnome-power-manager gnome-screenshot gnome-session gnome-session-canberra
  gnome-settings-daemon gnome-user-share gvfs-backends indicator-datetime
  indicator-power indicator-session indicator-sound invada-studio-plugins-lv2
  libbonoboui2-0 libbrasero-media3-1 libcanberra-gtk-module libcanberra-gtk0
  libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra0 libgnome2-0
  libgnome2-bin libgnome2-perl libgnomeui-0 libgnomevfs2-extra libpam-winbind
  librhythmbox-core5 libsmbclient libtdb1 lives mencoder metacity mplayer
  nautilus-sendto-empathy nautilus-share pavucontrol photofilmstrip pulseaudio
  pulseaudio-equalizer pulseaudio-module-jack pulseaudio-module-x11
  python-gnome2 python-smbc rawtherapee rhythmbox rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins samba-common-bin shutter
  smbclient soundconverter system-config-printer-common
  system-config-printer-gnome ubuntuone-client-gnome unity-2d unity-lens-music
  winbind
The following NEW packages will be installed:
  libtdb1:i386
0 upgraded, 1 newly installed, 83 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 36.5 kB of archives.
After this operation, 233 MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
```

That is strange.

2. After that, I had an error when I tried to start GuitarPro6:
```
QGtkStyle was unable to detect the current GTK+ theme.
Segmentation fault (core dumped)
```
Program shuts down instantly

I tried the solution from that topic:
[http://ubuntuforums.org/showthread.php?t=2099140](http://ubuntuforums.org/showthread.php?t=2099140)
but I had  *libgnome2-common* installed already.

---

### Post by matthew45 on 2014-12-03
I found another solution for that '*QGtkStyle was unable to detect the current GTK+ theme.*':
[http://paoloambrosio.net/2013/11/16/installing-guitarpro6-on-ubuntu-1310-saucy-64bit.html](http://paoloambrosio.net/2013/11/16/installing-guitarpro6-on-ubuntu-1310-saucy-64bit.html)

but after installing *gtk2-engines:i386* it's still not working, but now it's not shutting down, but freezes, and in terminal i can see this:

```
QGtkStyle was unable to detect the current GTK+ theme.

(process:2526): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.32.4/./gobject/gtype.c:2722: You forgot to call g_type_init()

(process:2526): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(process:2526): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.32.4/./gobject/gtype.c:2722: You forgot to call g_type_init()

(process:2526): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.32.4/./gobject/gtype.c:2722: You forgot to call g_type_init()

(process:2526): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.32.4/./gobject/gtype.c:2722: You forgot to call g_type_init()

(process:2526): GLib-GObject-CRITICAL **: g_type_add_interface_static:  assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(process:2526): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.32.4/./gobject/gtype.c:2722: You forgot to call g_type_init()

(process:2526): GLib-GObject-CRITICAL **:  g_type_interface_add_prerequisite: assertion `G_TYPE_IS_INTERFACE  (interface_type)' failed

(process:2526): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(process:2526): GLib-GObject-CRITICAL **: g_type_add_interface_static:  assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(process:2526): Gtk-CRITICAL **: IA__gtk_widget_style_get: assertion `GTK_IS_WIDGET (widget)' failed


```


Any solution?

---

