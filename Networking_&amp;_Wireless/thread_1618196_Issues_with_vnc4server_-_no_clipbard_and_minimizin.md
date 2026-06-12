---
title: "Issues with vnc4server - no clipbard and minimizing apps on &quot;d&quot;key press!"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by soundsk on 2010-11-10
Hi,

I setup an Ubuntu machine at home, to store mostly downloads. 

I installed and configured vnc4server to run on startup - Gnome Desktop, and disabled the default Ubuntu vnc server via the "Remote Desktop" menu.

It runs and i can access it fine, but when typing on any application, be it firefox or terminal, every time i press "D" the app minimizes itself!!

Also vncconfig is configured to accept clipboard transfer but it doesn't work...

Any idea why? 

This is truly annoying and makes the setup pretty much useless...

Here are config and log files...
Hope you can help!

Log File:
```
Xvnc Free Edition 4.1.1 - built Apr  9 2010 15:59:33
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc


Wed Nov 10 14:44:00 2010
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
gnome-session[1959]: WARNING: GSIdleMonitor: IDLETIME counter not found
gnome-session[1959]: WARNING: Unable to determine session: Unable to find session for cookie
GNOME_KEYRING_CONTROL=/tmp/keyring-VzTxbY
GNOME_KEYRING_PID=1981
GNOME_KEYRING_CONTROL=/tmp/keyring-VzTxbY
SSH_AUTH_SOCK=/tmp/keyring-VzTxbY/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-VzTxbY
SSH_AUTH_SOCK=/tmp/keyring-VzTxbY/ssh

** (gnome-settings-daemon:1986): WARNING **: Unable to start xrandr manager: RANDR extension is too old (must be at least 1.2)
The program 'gnome-power-manager' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 103 error_code 1 request_code 149 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Window manager warning: Log level 32: could not find XKB extension.

** (gnome-settings-daemon:1986): WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings

** (gnome-settings-daemon:1986): WARNING **: XKB extension not available

** (gnome-settings-daemon:1986): WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings

** (bluetooth-applet:2004): WARNING **: Could not open RFKILL control device, please verify your installation

(polkit-gnome-authentication-agent-1:2005): polkit-gnome-1-WARNING **: Unable to determine the session we are in: Remote Exception invoking org.freedesktop.ConsoleKit.Manager.GetSessionForUnixProcess() on /org/freedesktop/ConsoleKit/Manager at name org.freedesktop.ConsoleKit: org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to find session for cookie org.freedesktop.ConsoleKit.Manager.GeneralError Unable%20to%20find%20session%20for%20cookie
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Unable to find a synaptics device.
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
Initializing nautilus-gdu extension

** (nautilus:2003): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to find session for cookie

(nautilus:2003): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

Wed Nov 10 14:44:13 2010
 Connections: accepted: 0.0.0.0::2573
 SConnection: Client needs protocol version 3.4
 SConnection: Client uses unofficial protocol version 3.4
 SConnection: Assuming compatibility with version 3.3

Wed Nov 10 14:44:17 2010
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565

Wed Nov 10 14:44:18 2010
 VNCSConnST:  Client pixel format depth 8 (8bpp) bgr233
system-config-printer-applet: failed to start NewPrinterNotification service
** (update-notifier:2118): DEBUG: aptdaemon on bus: 0
** (update-notifier:2118): DEBUG: Skipping reboot required

Wed Nov 10 14:45:16 2010
 VNCSConnST:  Client pixel format depth 8 (8bpp) bgr233

Wed Nov 10 14:45:20 2010
 Connections: closed: 0.0.0.0::2573 (Clean disconnection)
 SMsgWriter:  framebuffer updates 150
 SMsgWriter:    ZRLE rects 275, bytes 54432
 SMsgWriter:    raw bytes equivalent 3854828, compression ratio 70.819150

Wed Nov 10 14:46:00 2010
 Connections: accepted: 0.0.0.0::2583
 SConnection: Client needs protocol version 3.4
 SConnection: Client uses unofficial protocol version 3.4
 SConnection: Assuming compatibility with version 3.3

Wed Nov 10 14:46:03 2010
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565
 VNCSConnST:  Client pixel format depth 8 (8bpp) bgr233
 VNCSConnST:  Client pixel format depth 8 (8bpp) bgr233

Wed Nov 10 14:49:02 2010
 Connections: closed: 0.0.0.0::2583 (Clean disconnection)
 SMsgWriter:  framebuffer updates 355
 SMsgWriter:    hextile rects 556, bytes 158599
 SMsgWriter:    ZRLE rects 2, bytes 7241
 SMsgWriter:    raw bytes equivalent 3226213, compression ratio 19.453769

Wed Nov 10 14:51:27 2010
 Connections: accepted: 0.0.0.0::2732
 SConnection: Client needs protocol version 3.4
 SConnection: Client uses unofficial protocol version 3.4
 SConnection: Assuming compatibility with version 3.3

Wed Nov 10 14:51:30 2010
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565
 VNCSConnST:  Client pixel format depth 8 (8bpp) bgr233

(nautilus:2003): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

Wed Nov 10 15:01:52 2010
 Connections: closed: 0.0.0.0::2732 (Clean disconnection)
 SMsgWriter:  framebuffer updates 380
 SMsgWriter:    ZRLE rects 661, bytes 99878
 SMsgWriter:    raw bytes equivalent 3709676, compression ratio 37.142073

```

Config File:
```
#!/bin/sh
# Uncomment the following two lines for normal desktop:
 unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
#xsetroot -solid grey
#vncconfig -iconic &
#x-window-manager &
gnome-session &

```

---

### Post by Azdour on 2010-11-29
Hi,

I've just started using vnc4server and had an issue with copying from my machine to the remote. It turns out I had to launch vncconfig and keep it open before the clipboard worked. If I closed the vncconfig window then my clipboard no longer worked.

---

### Post by scr9268 on 2011-03-28
I had the same minimize-on-"d" trbl with a relatively fresh installation of 10.10.

Searching the web, I came across [http://kosiara87.blogspot.com/2011/03/ubuntu-1010-vnc4server-pressing-d.html](http://kosiara87.blogspot.com/2011/03/ubuntu-1010-vnc4server-pressing-d.html) which said to do the following:

Change System->Preferences->Keyboard Shortcuts.

Find the shortcut titled "Hide all normal windows and set focus to the desktop" then change ‘D’ to something else.

---

I changed mine to Alt-2 and the "d" trbl went away.

Bill
[email]scr9268@yahoo.com[/email]

---

