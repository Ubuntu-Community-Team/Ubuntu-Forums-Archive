---
title: "Gmencoder and Gmyth"
date: 2007-09-30
forum: Multimedia Production
---

### Post by fain on 2007-09-30
I'm trying to get a Gmythstreamer server to stream live tv to my n800 via the instructions [here]("http://gmyth.sourceforge.net/wiki/index.php/GMythStreamer")
Steps 1 and 2 work fine but when I get to step 3 (transcode data) the gui pops up and just sits there nothing else happens. I'm using a mix of 32 bit packages and some built source on a 64 bit system btw.  gmencoder is a 64 bit package from getdeb.

heres the console output
```

user@ubuntu:~$ gmencoder -i myth://127.0.0.1:6543/livetv?channel=7 -o file:///home/user/channel7.avi

(gmencoder:7638): Gtk-CRITICAL **: gtk_widget_ref: assertion `GTK_IS_WIDGET (widget)' failed

(gmencoder:7638): Gtk-CRITICAL **: gtk_widget_set_size_request: assertion `height >= -1' failed
Loading configuration from [/home/user/.gmencoderrc]
Device DVD: [/dev/dvd].
UseAspectRatioPreviews DVD: [0].
AutoDetectPathMP: [1].
DeleteTemporalFiles: [1].
DeleteCopyToDiskFile: Not Found. Default Value [1].
Detected Mplayer/Mencoder Path [/usr/bin]
Loading TV configuration from []
Error opening the configuration file [].
Resutlado: Not Found. Default Value [-tv on].
Error opening the configuration file [].
UseAspectRatioPreviews: Not Found. Default Value [0].
Error opening the configuration file [].
AutoDetectPathMP: Not Found. Default Value [1].
Error opening the configuration file [].
DeleteTemporalFiles: Not Found. Default Value [1].
Error opening the configuration file [].
DeleteCopyToDiskFile: Not Found. Default Value [1].
Detected Mplayer/Mencoder Path [/usr/bin]

(gmencoder:7638): Gtk-WARNING **: FIXME we don't support GTK_JUSTIFY_FILL yet

(gmencoder:7638): Gtk-WARNING **: FIXME we don't support GTK_JUSTIFY_FILL yet

(gmencoder:7638): Gtk-WARNING **: FIXME we don't support GTK_JUSTIFY_FILL yet

(gmencoder:7638): Gtk-WARNING **: FIXME we don't support GTK_JUSTIFY_FILL yet

```
then it just sits there and does nothing.
theres a lot of configuration files missing where do i get them or how do i make them if this is even the problem?

---

### Post by renatofilho on 2007-10-04
Hi fain,

I don't know where you fond this gmencoder but this not is the correct program, Try download this from project page [http://gmyth.sourceforge.net/wiki/index.php/GMythStreamer](http://gmyth.sourceforge.net/wiki/index.php/GMythStreamer).

Renato

---

### Post by fain on 2007-10-04
Ok thanks renatofilho :)

Now im getting a error that says 

```
gmencoder: error while loading shared libraries: libgstbase-0.10.so.0: cannot open shared object file: No such file or directory
```

I'm assuming that it is because i only have the 64 bit gstreamer libraries.
if i build every thing from source would it work?
I was going to do that but some of the svn's listed [here]("http://gmyth.sourceforge.net/wiki/index.php/GMS_Howto") would not work.

---

