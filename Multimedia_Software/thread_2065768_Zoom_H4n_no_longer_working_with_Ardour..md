---
title: "Zoom H4n no longer working with Ardour."
date: 2012-10-02
forum: Multimedia Software
---

### Post by silverhaze06 on 2012-10-02
So I have my Zoom H4n that I want to interface with Ardour. But when I try to use it with Ardour, it says it can not start jack. 

It worked fine a few months ago before I had to re-install Ubuntu. Any other threads I find with the same problem are super old and have no replies. The zoom will show up in the sound settings menu with out a problem tho. So, I am totally lost at this point. Any help is greatly appreciated!

---

### Post by silverhaze06 on 2012-10-02
heres my output from qjackctl

```
18:15:49.207 Patchbay deactivated.
18:15:49.209 Statistics reset.
18:15:49.243 ALSA connection change.
18:15:49.270 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot read socket fd = 32 err = Success
JackSocketClientChannel read fail
Cannot open qjackctl client
18:15:54.290 ALSA connection graph change.
18:16:07.058 D-BUS: JACK server could not be started. Sorry
Cannot read socket fd = 32 err = Success
JackSocketClientChannel read fail
Cannot open qjackctl client
(qjackctl.real:5451): Gtk-WARNING **: Theme directory actions/16 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory animations/16 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory apps/16 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory categories/16 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory devices/16 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory emblems/16 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory mimetypes/16 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory places/16 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory status/16 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory stock/16 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory actions/22 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory animations/22 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory apps/22 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory categories/22 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory devices/22 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory emblems/22 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory mimetypes/22 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory places/22 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory status/22 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory stock/22 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory actions/24 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory animations/24 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory apps/24 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory categories/24 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory devices/24 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory emblems/24 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory mimetypes/24 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory places/24 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory status/24 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory stock/24 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory actions/32 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory animations/32 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory apps/32 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory categories/32 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory devices/32 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory emblems/32 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory mimetypes/32 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory places/32 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory status/32 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory stock/32 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory actions/48 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory animations/48 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory apps/48 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory categories/48 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory devices/48 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory emblems/48 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory mimetypes/48 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory places/48 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory status/48 of theme uniwhite has no size field
(qjackctl.real:5451): Gtk-WARNING **: Theme directory stock/48 of theme uniwhite has no size field
Tue Oct  2 18:16:07 2012: Starting jack server...
Tue Oct  2 18:16:07 2012: [1m[31mERROR: `default' server already active[0m
Tue Oct  2 18:16:07 2012: [1m[31mERROR: Failed to open server[0m
Tue Oct  2 18:16:08 2012: Saving settings to "/home/nate/.config/jack/conf.xml" ...
18:16:17.332 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
Cannot read socket fd = 32 err = Success
JackSocketClientChannel read fail
Cannot open qjackctl client
18:17:23.556 D-BUS: JACK server could not be started. Sorry
Cannot read socket fd = 32 err = Success
Cannot open qjackctl client
Tue Oct  2 18:17:23 2012: Starting jack server...
Tue Oct  2 18:17:23 2012: [1m[31mERROR: `default' server already active[0m
Tue Oct  2 18:17:23 2012: [1m[31mERROR: Failed to open server[0m
Tue Oct  2 18:17:24 2012: Saving settings to "/home/nate/.config/jack/conf.xml" ...
18:17:32.588 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
Cannot read socket fd = 32 err = Success
JackSocketClientChannel read fail
Cannot open qjackctl client
```

I also found this thread, [http://ardour.org/node/2964]("http://ardour.org/node/2964") but I have no idea what they're talking about with all the linux code stuff.

---

### Post by silverhaze06 on 2012-10-04
I figured out most of the other thread and it still doesn't want to work. Anyone know whats going on? Because I don't... ](*,)

---

