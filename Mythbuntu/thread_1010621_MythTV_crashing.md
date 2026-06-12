---
title: "MythTV crashing"
date: 2008-12-13
forum: Mythbuntu
---

### Post by patrick0605 on 2008-12-13
I was doing some tinkering trying to install the newest mythprime version, because I'm still having recording issues.  Regardless, I'm still a total beginner to this stuff, so I really no clue what I did.  I fiddled a bit in the terminal trying to install the new version, but couldn't, so I decided to restart and just forget it.  Now when I restart, I get this:

```
/etc/gdm/Xsession: Beginning session setup...
13/12/2008 23:49:22 passing arg to libvncserver: -rfbauth
13/12/2008 23:49:22 passing arg to libvncserver: /root/.vnc/passwd
13/12/2008 23:49:22 passing arg to libvncserver: -rfbport
13/12/2008 23:49:22 passing arg to libvncserver: 5900
13/12/2008 23:49:22 x11vnc version: 0.9.3 lastmod: 2007-09-30
13/12/2008 23:49:22 Using X display :0
13/12/2008 23:49:22 
13/12/2008 23:49:22 ------------------ USEFUL INFORMATION ------------------
13/12/2008 23:49:22 X DAMAGE available on display, using it for polling hints.
13/12/2008 23:49:22   To disable this behavior use: '-noxdamage'
13/12/2008 23:49:22 
13/12/2008 23:49:22 XFIXES available on display, resetting cursor mode
13/12/2008 23:49:22   to: '-cursor most'.
13/12/2008 23:49:22   to disable this behavior use: '-cursor arrow'
13/12/2008 23:49:22   or '-noxfixes'.
13/12/2008 23:49:22 using XFIXES for cursor drawing.
13/12/2008 23:49:22 GrabServer control via XTEST.
13/12/2008 23:49:22 
13/12/2008 23:49:22 Scroll Detection: -scrollcopyrect mode is in effect to
13/12/2008 23:49:22   use RECORD extension to try to detect scrolling windows
13/12/2008 23:49:22   (induced by either user keystroke or mouse input).
13/12/2008 23:49:22   If this yields undesired behavior (poor response, painting
13/12/2008 23:49:22   errors, etc) it may be disabled via: '-noscr'
13/12/2008 23:49:22   Also see the -help entry for tuning parameters.
13/12/2008 23:49:22   You can press 3 Alt_L's (Left "Alt" key) in a row to 
13/12/2008 23:49:22   repaint the screen, also see the -fixscreen option for
13/12/2008 23:49:22   periodic repaints.
13/12/2008 23:49:22 
13/12/2008 23:49:22 XKEYBOARD: number of keysyms per keycode 6 is greater
13/12/2008 23:49:22   than 4 and 287 keysyms are mapped above 4.
13/12/2008 23:49:22   Automatically switching to -xkb mode.
13/12/2008 23:49:22   If this makes the key mapping worse you can
13/12/2008 23:49:22   disable it with the "-noxkb" option.
13/12/2008 23:49:22   Also, remember "-remap DEAD" for accenting characters.
13/12/2008 23:49:22 X FBPM extension not supported.
13/12/2008 23:49:22 X display is capable of DPMS.
13/12/2008 23:49:22 --------------------------------------------------------
13/12/2008 23:49:22 
13/12/2008 23:49:22 Default visual ID: 0x23
13/12/2008 23:49:22 Read initial data from X display into framebuffer.
13/12/2008 23:49:22 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/4096
13/12/2008 23:49:22 
13/12/2008 23:49:22 X display :0.0 is 32bpp depth=24 true color
13/12/2008 23:49:22 
13/12/2008 23:49:22 Listening for VNC connections on TCP port 5900
13/12/2008 23:49:22 
13/12/2008 23:49:22 Xinerama is present and active (e.g. multi-head).
13/12/2008 23:49:22 Xinerama: enabling -xwarppointer mode to try to correct
13/12/2008 23:49:22 Xinerama: mouse pointer motion. XTEST+XINERAMA bug.
13/12/2008 23:49:22 Xinerama: Use -noxwarppointer to force XTEST.
13/12/2008 23:49:22 fb read rate: 544 MB/sec
13/12/2008 23:49:22 screen setup finished.
13/12/2008 23:49:22 

The VNC desktop is:      MythBox:0
PORT=5900

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

more info: http://www.karlrunge.com/x11vnc/#faq-client-caching

/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 10 overrides entry on line 7
Agent pid 6920
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found

** (xfce-mcs-manager:6927): WARNING **: display_plugin: Unable to configure display resolution
** Message: another SSH agent is running at: /tmp/ssh-oEsftK6919/agent.6919
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead

** (nm-applet:7005): WARNING **: No connections defined

** (update-notifier:6995): WARNING **: already running?

Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead

** (update-notifier:7016): WARNING **: already running?


** (nm-applet:7027): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:7027): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
2008-12-13 23:49:25.195 Using runtime prefix = /usr
2008-12-13 23:49:25.199 Using runtime prefix = /usr
QServerSocket: failed to bind or listen to the socket
2008-12-13 23:49:25.200 MediaRenderer::HttpServer Create Error
2008-12-13 23:49:25.213 XScreenSaver support enabled
2008-12-13 23:49:25.213 DPMS is active.
2008-12-13 23:49:25.213 Empty LocalHostName.
2008-12-13 23:49:25.213 Using localhost value of MythBox
2008-12-13 23:49:25.219 New DB connection, total: 1
2008-12-13 23:49:25.223 Connected to database 'mythconverg' at host: localhost
2008-12-13 23:49:25.224 Closing DB connection named 'DBManager0'
2008-12-13 23:49:25.229 Primary screen 0.
2008-12-13 23:49:25.229 Connected to database 'mythconverg' at host: localhost
2008-12-13 23:49:25.239 Using screen 0, 1024x768 at 0,0

** (update-notifier:7089): WARNING **: already running?


** (update-notifier:7071): WARNING **: already running?

Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead

** (nm-applet:7096): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:7096): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
2008-12-13 23:49:25.736 Using runtime prefix = /usr
QServerSocket: failed to bind or listen to the socket
2008-12-13 23:49:25.757 XScreenSaver support enabled
2008-12-13 23:49:25.762 DPMS is active.
2008-12-13 23:49:25.762 Empty LocalHostName.
2008-12-13 23:49:25.762 Using localhost value of MythBox
2008-12-13 23:49:25.775 MediaRenderer::HttpServer Create Error
2008-12-13 23:49:25.788 New DB connection, total: 1
2008-12-13 23:49:25.830 Connected to database 'mythconverg' at host: localhost
2008-12-13 23:49:25.831 Closing DB connection named 'DBManager0'
2008-12-13 23:49:25.887 Primary screen 0.
2008-12-13 23:49:25.887 Connected to database 'mythconverg' at host: localhost
2008-12-13 23:49:25.888 Using screen 0, 1024x768 at 0,0
2008-12-13 23:49:25.922 XScreenSaver support enabled
2008-12-13 23:49:25.924 DPMS is active.
2008-12-13 23:49:25.924 Empty LocalHostName.
2008-12-13 23:49:25.924 Using localhost value of MythBox
2008-12-13 23:49:25.929 New DB connection, total: 1
2008-12-13 23:49:25.939 Connected to database 'mythconverg' at host: localhost
2008-12-13 23:49:25.982 Closing DB connection named 'DBManager0'
2008-12-13 23:49:25.988 Primary screen 0.
2008-12-13 23:49:25.991 Connected to database 'mythconverg' at host: localhost
2008-12-13 23:49:25.996 Using screen 0, 1024x768 at 0,0

(xfwm4:6954): libxfcegui4-WARNING **: ICE I/O Error

(xfwm4:6954): libxfcegui4-WARNING **: Disconnected from session manager.

(xfce4-panel:6964): libxfcegui4-WARNING **: ICE I/O Error

(xfce4-panel:6964): libxfcegui4-WARNING **: Disconnected from session manager.

(xfdesktop:6957): libxfcegui4-WARNING **: ICE I/O Error

(xfdesktop:6957): libxfcegui4-WARNING **: Disconnected from session manager.
Segmentation fault
Agent pid 6920 killed

```

Anyone have any insight on what this means?  When I hit ok to clear the error message, my session ends and I'm at the login screen.

Thanks,

Patrick

---

### Post by ian dobson on 2008-12-14
Hi,

Could it be that you've got VNC setup? Could you try disabling it to see if a "bare" system work.

Regards
Ian Dobson

---

### Post by patrick0605 on 2008-12-14
> **ian dobson said:**
> Hi,

Could it be that you've got VNC setup? Could you try disabling it to see if a "bare" system work.

Regards
Ian Dobson


Yep did that, still getting the message.

My guess is that I did something to the way ubuntu starts, only on my MythTV session, the regular GNOME desktop starts no problem.

Any other thoughts?  I'm getting so tired of having to fiddle with this every day just so I can record programs, please help.

---

