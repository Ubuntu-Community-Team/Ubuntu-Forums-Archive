---
title: "knowing when you remote login"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by w0296094 on 2010-02-09
i recently installed    	 	 	 	 	**x11vnc vnc-java. **to my computer, and vinagre to my computer, and both computers are working fine. However, x11vnc does not seem to inform you when another computer is logged in to your system. How do you identify if a computer is remotely logged in to your system?
BTW i have kubuntu 8.10

---

### Post by krunge on 2010-02-09
x11vnc has a minimal gui mode.  For it to work you need to make sure the "tk" package is installed.

A simple way to start up the gui is **after** the x11vnc server is running, then run this command from a terminal inside your desktop: ```
x11vnc -gui connect,tray
``` This should make a tray icon that will indicate if someone is accessing the desktop remotely; and has other features.

You can also add "-gui tray" to the initial x11vnc cmdline if you like.

From the command line (again after the x11vnc server is running) you can get a list of connected clients this way by typing this in a terminal inside your desktop:
```

# x11vnc -Q clients
>>> sending remote command: "qry=clients" via X11VNC_REMOTE X property.
aro=clients:0x1:10.0.2.1:43824:runge:none:haystack.runge.home:KMBCF:0:1265735992

``` this way does not require the "tk" package.

---

