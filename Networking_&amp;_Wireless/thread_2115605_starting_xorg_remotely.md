---
title: "starting xorg remotely?"
date: 2013-02-13
forum: Networking &amp; Wireless
---

### Post by KisteBecks on 2013-02-13
hi,

is there a way to remotely login to a remote host's xorg when no user is logged in?

ive experimented a bit, but it looks like that vino was made for a user already logged in...is that correct?

is there another way to get xorg running on a remote system without being physically present at the host?


looks like this:
[http://gpio.kaltpost.de/?page_id=84](http://gpio.kaltpost.de/?page_id=84)
should work, but out of the box it doesnt.

starting xfvb
```

Xvfb -screen 1 1024x768x16 -ac
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/100dpi/:unscaled, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/75dpi/:unscaled, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/100dpi, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/75dpi, removing from list!
[dix] Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!

```starting fluxbox (outputs quite a log "setting default value" lines, this is just a short snippet)
```

DISPLAY=:0 fluxbox
Setting default value
Failed to read: session.screen1.toolbar.tools
Setting default value
Failed to read: session.screen1.iconbar.mode
Setting default value
Failed to read: session.screen1.iconbar.alignment
Setting default value
Failed to read: session.screen1.iconbar.iconWidth
Setting default value
Failed to read: session.screen1.iconbar.iconTextPadding
Setting default value
Failed to read: session.screen1.iconbar.usePixmap
Setting default value
Failed to read: session.screen1.strftimeFormat
Setting default value
...

```starting the vnc server
```

x11vnc -display :0
#starts it without a password

```now when i connect to this machine with tightvncviewer from win7 the program crashed a second after connect


x11vnc error:
```

13/02/2013 18:23:10 Got connection from client 192.168.29.44
13/02/2013 18:23:10   other clients:
13/02/2013 18:23:10 Disabled X server key autorepeat.
13/02/2013 18:23:10   to force back on run: 'xset r on' (3 times)
13/02/2013 18:23:10 incr accepted_client=1 for 192.168.29.44:50476  sock=12
13/02/2013 18:23:10 Client Protocol Version 3.8
13/02/2013 18:23:10 Protocol version sent 3.8, using 3.8
13/02/2013 18:23:10 rfbProcessClientSecurityType: executing handler for type 1
13/02/2013 18:23:10 rfbProcessClientSecurityType: returning securityResult for client rfb version >= 3.8
13/02/2013 18:23:12 rfbProcessClientNormalMessage: read: Connection reset by peer
13/02/2013 18:23:12 client_count: 0
13/02/2013 18:23:12 Restored X server key autorepeat to: 1
13/02/2013 18:23:12 viewer exited.
13/02/2013 18:23:12 deleted 40 tile_row polling images.

```if i start xfvb like this:
```

x11vnc -nofb -visual TrueColor -display :0

```tightvnc displays a black screen, ive tried this in combination with:
```

Xvfb -screen 1 1024x768x24 -ac
Xvfb -screen 1 1024x768x16 -ac
Xvfb -screen 1 1024x768x8 -ac

```nothing but a black screen

---

