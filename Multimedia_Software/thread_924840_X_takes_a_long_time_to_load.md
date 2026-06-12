---
title: "X takes a long time to load"
date: 2008-09-20
forum: Multimedia Software
---

### Post by devosion on 2008-09-20
Im setting up a laptop running intels 82852/855GM card and I am having problems with a long load with a black screen from X upon startup. First it mentioned that xgl wasnt present so I installed that, but had no success in speeding up the load time(which is about a 80 seconds). This also made x run slower than it had without xgl. I uninstalled xgl and ran fixX from recovery mode and the problem still persists.

When I view .xsession-errors two errors stick out.

> 
** (nautilus:5824): WARNING **: Unable to add monitor: Not supported
Starting gtk-window-decorator

(gnome-panel:5823): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -12 and height 24
I/O warning : failed to load external entity "/home/devosion/.compiz/session/default0"


Also in my xorg.conf file nothing is setup. 

> 
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Synaptics Touchpad"
EndSection


---

