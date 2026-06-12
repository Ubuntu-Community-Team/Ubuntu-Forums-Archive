---
title: "Latest updates broke my myth!"
date: 2010-01-21
forum: Mythbuntu
---

### Post by singedwings on 2010-01-21
I just did the latest automatic updates on my system (probably released today 21/1/2010) and now when I try to start either the frontend or the setup I cannot see the menus.

```
tv@tellybox:~$ mythfrontend
2010-01-21 18:06:11.446 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-01-21 18:06:11.476 AudioPulseUtil: Suspend Success
2010-01-21 18:06:11.476 Using runtime prefix = /usr
2010-01-21 18:06:11.476 Using configuration directory = /home/tv/.mythtv
2010-01-21 18:06:11.947 Empty LocalHostName.
2010-01-21 18:06:11.948 Using localhost value of tellybox
2010-01-21 18:06:11.959 New DB connection, total: 1
2010-01-21 18:06:11.965 Connected to database 'mythconverg' at host: localhost
2010-01-21 18:06:11.966 Closing DB connection named 'DBManager0'
2010-01-21 18:06:11.986 ScreenSaverX11Private: Gnome screen saver support enabled
2010-01-21 18:06:11.996 DPMS is active.
2010-01-21 18:06:11.997 Primary screen: 0.
2010-01-21 18:06:11.998 Connected to database 'mythconverg' at host: localhost
2010-01-21 18:06:12.000 Using screen 0, 1280x1024 at 0,0
2010-01-21 18:06:12.028 MythUI Image Cache size set to 20971520 bytes
2010-01-21 18:06:12.029 Enabled verbose msgs:  important general
2010-01-21 18:06:12.040 Primary screen: 0.
2010-01-21 18:06:12.040 Using screen 0, 1280x1024 at 0,0
2010-01-21 18:06:12.042 Using theme base resolution of 1280x720
2010-01-21 18:06:12.056 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-01-21 18:06:12.056 JoystickMenuThread Error: Joystick disabled - Failed to read /home/tv/.mythtv/joystickmenurc
2010-01-21 18:06:12.273 Using the OpenGL painter
QGLContext::makeCurrent(): Cannot make invalid context current.
2010-01-21 18:06:12.387 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2010-01-21 18:06:12.392 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2010-01-21 18:06:12.398 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2010-01-21 18:06:12.399 Unable to load window 'backgroundwindow' from base
2010-01-21 18:06:12.427 Current MythTV Schema Version (DBSchemaVer): 1244
2010-01-21 18:06:12.594 Desktop video mode: 1280x1024 85.0268 Hz
2010-01-21 18:06:12.712 Registering Internal as a media playback plugin.
2010-01-21 18:06:12.713 No plugins directory /usr/lib/mythtv/plugins
2010-01-21 18:06:12.726 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-01-21 18:06:12.734 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-01-21 18:06:12.738 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-01-21 18:06:12.753 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-01-21 18:06:12.804 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-01-21 18:06:12.806 Found mainmenu.xml for theme 'Mythbuntu'
QGLContext::makeCurrent(): Cannot make invalid context current.
QGLContext::makeCurrent(): Cannot make invalid context current.
2010-01-21 18:06:13.661 MythContext: Connecting to backend server: 192.168.0.5:6543 (try 1 of 1)
2010-01-21 18:06:13.663 Using protocol version 50
QGLContext::makeCurrent(): Cannot make invalid context current.
QGLContext::makeCurrent(): Cannot make invalid context current.
QGLContext::makeCurrent(): Cannot make invalid context current.
QGLContext::makeCurrent(): Cannot make invalid context current.
QGLContext::makeCurrent(): Cannot make invalid context current.
QPainter::begin: Paint device returned engine == 0, type: 3
QPainter::setFont: Painter not active
QPainter::setPen: Painter not active
QPainter::end: Painter not active, aborted
QImage::scaled: Image is a null image
QGLContext::makeCurrent(): Cannot make invalid context current.
QGLContext::makeCurrent(): Cannot make invalid context current.
QGLContext::makeCurrent(): Cannot make invalid context current.
QGLContext::makeCurrent(): Cannot make invalid context current.
QGLContext::makeCurrent(): Cannot make invalid context current.
QGLContext::makeCurrent(): Cannot make invalid context current.
```

I was able to get the menus back by doing ```
mythfrontend -O ThemePainter=qt*

``` and then changing the painter back to qt from opengl, but this means I am not running with my preferred method of opengl. If anyone knows how to fix this rather than the workaround I have shown please post.

---

### Post by superm1 on 2010-01-22
You're gonna have to be more specific on latest updates.  What updates did you do?  You can investigate /var/log/dpkg.log and /var/log/apt/term.log and /var/log/apt/term/history.log to get a better idea.

---

### Post by johnnybirdman on 2010-01-23
I applied the latest updates via apt-get upgrade and I'm also having problems now with no sound from my digital optical out.
From the looks of the some of the posts recently we are not the only one's.
J.

---

### Post by SnafuFlux on 2010-02-15
> **johnnybirdman said:**
> I applied the latest updates via apt-get upgrade and I'm also having problems now with no sound from my digital optical out.
From the looks of the some of the posts recently we are not the only one's.
J.

was it only analog sources?  or was it both digital/dts/analog?  only analog doesn't work for me

---

### Post by johnnybirdman on 2010-02-16
> **SnafuFlux said:**
> was it only analog sources?  or was it both digital/dts/analog?  only analog doesn't work for me

audio over hdmi was working (dvi to hdmi --2 pins off my soundcard to my xfx 8600xx) but DTS and optical out stopped working.

This was resolved for me by doing a complete reinstall, applied all apt-get updates and everything is working fine.
No clue what the update changed that caused it to go wacky.
J.

---

