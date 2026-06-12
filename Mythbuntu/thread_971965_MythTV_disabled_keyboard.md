---
title: "MythTV disabled keyboard"
date: 2008-11-05
forum: Mythbuntu
---

### Post by Mike-97470 on 2008-11-05
I installed Mythbuntu/MythTV a few days ago and have spent a few hours trying to get it working with my PVR-150 TV card.  As of now the Nvidia driver is enabled and the X Server is working, I think.  The most serious problem is that whenever MythTV frontend/backend/setup runs, my keyboard is disabled as well as the mouse buttons although the scroll wheel works fine.  That pretty much means that a reboot is required since MythTV is full screen, I haven't figured out how to kill it.  The exception is when "Mythubuntu Control Centre" is run from the System menu: then the keyboard/mouse work ok, the TV card is detected and the channel scan works.

I think the backend is running ok now, but the frontend has errors, maybe because I've never been able to run setup on it without a keyboard.  Anyway, here are the logs:

Backend
2008-11-05 09:05:45.545 Using runtime prefix = /usr
2008-11-05 09:05:45.830 Empty LocalHostName.
2008-11-05 09:05:46.446 Using localhost value of mike-desktop
2008-11-05 09:05:46.994 New DB connection, total: 1
2008-11-05 09:05:47.156 Connected to database 'mythconverg' at host: localhost
2008-11-05 09:05:47.209 Closing DB connection named 'DBManager0'
2008-11-05 09:05:47.393 Connected to database 'mythconverg' at host: localhost
2008-11-05 09:05:47.529 New DB connection, total: 2
2008-11-05 09:05:47.630 Connected to database 'mythconverg' at host: localhost
2008-11-05 09:05:47.727 Current Schema Version: 1214
Starting up as the master server.
2008-11-05 09:05:47.810 New DB connection, total: 3
2008-11-05 09:05:47.882 Connected to database 'mythconverg' at host: localhost
2008-11-05 09:05:48.046 New DB scheduler connection
2008-11-05 09:05:48.148 Connected to database 'mythconverg' at host: localhost
2008-11-05 09:05:48.325 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-11-05 09:05:48.344 Main::Registering HttpStatus Extension
2008-11-05 09:05:48.359 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-05 09:05:48.391 Enabled verbose msgs:  important general
2008-11-05 09:05:48.428 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-05 09:05:51.173 Reschedule requested for id -1.
2008-11-05 09:05:51.201 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2008-11-05 09:05:51.207 Seem to be woken up by USER
2008-11-05 09:06:28.791 MainServer::HandleAnnounce Monitor
2008-11-05 09:06:28.799 adding: mike-desktop as a client (events: 0)
2008-11-05 09:06:28.799 MainServer::HandleAnnounce Monitor
2008-11-05 09:06:28.800 adding: mike-desktop as a client (events: 1)
2008-11-05 09:07:08.174 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range

Frontend
Starting mythfrontend.real..
2008-11-05 09:03:23.057 New DB connection, total: 2
2008-11-05 09:03:23.057 Connected to database 'mythconverg' at host: localhost
2008-11-05 09:03:23.059 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-05 09:03:23.059 Enabled verbose msgs:  important general
2008-11-05 09:03:23.305 No theme dir: /home/mike/.mythtv/themes/G.A.N.T
2008-11-05 09:03:23.306 Primary screen 0.
2008-11-05 09:03:23.306 Using screen 0, 1152x864 at 0,0
2008-11-05 09:2008-11-05 09:05:45.545 Using runtime prefix = /usr
2008-11-05 09:05:45.830 Empty LocalHostName.
2008-11-05 09:05:46.446 Using localhost value of mike-desktop
2008-11-05 09:05:46.994 New DB connection, total: 1
2008-11-05 09:05:47.156 Connected to database 'mythconverg' at host: localhost
2008-11-05 09:05:47.209 Closing DB connection named 'DBManager0'
2008-11-05 09:05:47.393 Connected to database 'mythconverg' at host: localhost
2008-11-05 09:05:47.529 New DB connection, total: 2
2008-11-05 09:05:47.630 Connected to database 'mythconverg' at host: localhost
2008-11-05 09:05:47.727 Current Schema Version: 1214
Starting up as the master server.
2008-11-05 09:05:47.810 New DB connection, total: 3
2008-11-05 09:05:47.882 Connected to database 'mythconverg' at host: localhost
2008-11-05 09:05:48.046 New DB scheduler connection
2008-11-05 09:05:48.148 Connected to database 'mythconverg' at host: localhost
2008-11-05 09:05:48.325 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-11-05 09:05:48.344 Main::Registering HttpStatus Extension
2008-11-05 09:05:48.359 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-05 09:05:48.391 Enabled verbose msgs:  important general
2008-11-05 09:05:48.428 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-05 09:05:51.173 Reschedule requested for id -1.
2008-11-05 09:05:51.201 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2008-11-05 09:05:51.207 Seem to be woken up by USER
2008-11-05 09:06:28.791 MainServer::HandleAnnounce Monitor
2008-11-05 09:06:28.799 adding: mike-desktop as a client (events: 0)
2008-11-05 09:06:28.799 MainServer::HandleAnnounce Monitor
2008-11-05 09:06:28.800 adding: mike-desktop as a client (events: 1)
2008-11-05 09:07:08.174 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range03:23.306 No theme dir: /home/mike/.mythtv/themes/G.A.N.T
2008-11-05 09:03:23.307 Switching to square mode (G.A.N.T)
2008-11-05 09:03:23.319 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-11-05 09:03:23.319 lirc_init failed for mythtv, see preceding messages
2008-11-05 09:03:23.319 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mike/.mythtv/joystickmenurc
2008-11-05 09:03:23.866 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2008-11-05 09:03:23.915 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-05 09:03:23.948 Registering Internal as a media playback plugin.
2008-11-05 09:03:24.002 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-05 09:03:24.078 MythMusic adding CD-Writer: 2,1,0 -- CD/DVDW SH-S182M
2008-11-05 09:03:24.103 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.102:5060 NAT address 192.168.1.102
SIP: Cannot register; proxy, username or password not set
2008-11-05 09:03:24.163 No theme dir: /home/mike/.mythtv/themes/G.A.N.T

Any advice on what to try next will be much appreciated! Thanks, Mike

---

### Post by Mike-97470 on 2008-11-07
I'm wondering if MythTV's frontend/backend idea and the resulting use of X-server may be the source of the keyboard lock problem I'm having.  How does this look for xorg.conf?

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by novellahub on 2008-11-07
Add the following to your xorg.conf file in the device section

```
Option "UseEvents" "True"
```

```
Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
Option "UseEvents" "True"
EndSection
```

Reboot and then see what the results are.  Also check our playback profile.  I had trouble with playback my machine set at "cpu+".  I have mine set at "cpu++" now.

---

