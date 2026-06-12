---
title: "Exaile"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by koulanji on 2007-10-28
So I love how I get my new shiny ubuntu and I can't open many of the apps on here like exaile

When I type it in the terminal I get 

exaile
Traceback (most recent call last):
  File "exaile.py", line 44, in <module>
    import gtk, gtk.glade, pango, dbus
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

As well as my software sources too

gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
  File "/usr/bin/software-properties-gtk", line 27, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

I've realized that this is the same error. Any suggestions? 

Keep up the good work and thanks

Jason

---

### Post by Gremlinzzz on 2007-10-28
try
sudo apt-get autoremove exaile
then go to home folder click view check show hidden files if theres a exaile folder there delete it. then
sudo aptitude install exaile
the launch icon will be on the menu:guitar:

---

### Post by koulanji on 2007-10-29
Same error buddy.

---

### Post by kshane on 2007-10-29
> **koulanji said:**
> Same error buddy.

I had a similar problem.  I used Synaptic to "Completely Remove" and then installed, again with Synaptic.  The GUI install seemed to work better for me...

Kevin

---

### Post by koulanji on 2007-10-30
Same command line output[axisaudio@axisaudio-desktop:~$ exaile
Traceback (most recent call last):
  File "exaile.py", line 44, in <module>
    import gtk, gtk.glade, pango, dbus
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents
axisaudio@axisaudio-desktop:~$ 
] after I did that. It just does not work.

---

### Post by rosswmcgee on 2007-10-31
Try this- 

dont forget to run these commands before your reinstall
sudo apt-get remove
sudo apt-get autoremove
sudo apt-get clean

Then re-install 
Make sure you have the gstreamers.

---

### Post by koulanji on 2007-11-03
I do have the gstreamers, but I still get these python and cairo errors when I try to run it

Traceback (most recent call last):
  File "exaile.py", line 44, in <module>
    import gtk, gtk.glade, pango, dbus
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

---

### Post by abandonedthe_mulletator on 2008-01-01
I have the same problem.
I has something to do with my WiiMote.

Here's a post on another forum about this
[http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/package-updater-crashes-and-other-problems-fc7-dell-inspiron-608490/#post2998694]("http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/package-updater-crashes-and-other-problems-fc7-dell-inspiron-608490/#post2998694")

It has something to do with this command:
```
ldconfig /usr/local/lib/
```

Any advice?

---

