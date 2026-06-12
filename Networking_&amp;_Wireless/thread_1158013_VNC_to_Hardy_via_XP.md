---
title: "VNC to Hardy via XP"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by greazy on 2009-05-13
hello all.  Its been a while (so long I forgot my old login).

I'm sure my issue has been resolved elsewhere so feel free to share a link if necessary.  I've read through dozens of potential solutions but I always run into a wall; and have to jump ship and search again.  Alas, I feel it is time to lay-out my rather simple issue here to get it resolved.

GOAL
Remote VNC connection from XP machine to Hardy Server (w/ ubuntu desktop/gdm installed).

METHOD
PuTTy to Server, turn-on vino (or alternative?), then engage VNCviewer.

ISSUES
1.  I don't want to be logged into the Server all the time (necessary for Gnome's remote desktop); I want to be able to log-out but still able to VNC in (by turning on via PuTTy if needed).  I am quite successful VNCing to the Server via my XP machine when I'm already logged into the server.  
2.  I don't plan on keeping a mouse/keyboard/monitor attached to the server.
3.  Reboots will log me out, so the standard Gnome method of using vino will die.

POOR ATTEMPTS
1.  I've tried configuring PuTTy to "Enable X11 forwarding" to 127.0.0.1 and launching Xming; I get a greyish X11 screen (reminds me of my solaris days) and no desktop.
2.  I've tried launching vino through Putty (vino-server from /usr/lib/vino/vino-server) but I get:
> PuTTY X11 proxy: wrong authentication protocol attempted
(vino-server:6338): Gtk-WARNING **: cannot open display: localhost:10.0
I've thought about installing a different vnc server like tightvnc but I haven't done so yet.  I'm also thinking that I'd rather NOT have VNC running in the background (at boot) but that it would only start when I PuTTy in and launch it...but at this point I'd consider it.

thoughts?  Help?  Links?  Questions?  I'm all ears.

Thanks for reading,

Greazy

---

### Post by greazy on 2009-05-15
~ping~

---

