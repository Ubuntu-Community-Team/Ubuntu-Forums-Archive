---
title: "launching totem over ssh"
date: 2009-05-01
forum: Multimedia Software
---

### Post by yelirekim on 2009-05-01
Does anyone have any experience trying to get totem to launch over ssh?  I figured it would be as easy as just giving it the right X window to show up on, but I'm not having any luck and I'm kinda scratching my head as to what exactly is going on with it:

```

mike@mpc:~$ totem --display :0.0
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Not running within active session)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Not running within active session)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Not running within active session)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Not running within active session)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Not running within active session)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Not running within active session)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Not running within active session)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Not running within active session)

** (totem:3402): WARNING **: gst_gconf_get_string: error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Not running within active session)


** (totem:3402): WARNING **: gst_gconf_get_string: error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Not running within active session)

** Message: Error: Could not initialise Xv output
xvimagesink.c(1668): gst_xvimagesink_xcontext_get (): /GstXvImageSink:autovideosink0-actual-sink-xvimage:
Could not open display

** Message: Error: Could not initialize supporting library.
gstautovideosink.c(367): gst_auto_video_sink_detect (): /GstGConfVideoSink:video-sink/GstAutoVideoSink:autovideosink0:
Failed to find a supported video sink

** Message: Error: Could not initialise X output
ximagesink.c(1188): gst_ximagesink_xcontext_get (): /GstXImageSink:video-sink:
Could not open display

```

The weird thing is that this correctly identifies my x window session and launches totem on the remote machine, causing it to display, but it also has a dialog box covering it saying "Could not initialise Xv output".

Any help would be much appreciated.

---

### Post by eudoxos on 2009-05-09
[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/367169](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/367169) has the solution: ~/.dbus is not owned by you but root (maybe after running some X11 app through sudo? no idea). Just do

sudo chown -R yourusername: ~/.dbus

It worked for me very nicely.

---

### Post by fuzzyworbles on 2010-01-11
same problem here, and changing the ~/.dbus ownership didn't help.

---

### Post by 3doff on 2011-03-13
Use 
```
export DISPLAY=:0.0
```
works fine with me

---

### Post by cipherboy_loc on 2011-03-13
I think if you sign in regularly (through GDM), you can then SSH in and launch totem. What I think your issue is is that because you have not logged in with a GNOME (KDE, XFCE, etc) Session, gconf is not running. Though I don't know that you have not signed in already... Why I think that you have not signed is because it says:

> 
Details -  1: Not running within active session


Though also, it could mean that you are signed into GNOME, but gconf crashed (doesn't really make sense to me, just putting it forward)... 


If none of this works, try removing /tmp/orbit-*, which I think is what I did when I encountered similar issues (except from a local terminal wondering why nothing would open).



Cipherboy

---

