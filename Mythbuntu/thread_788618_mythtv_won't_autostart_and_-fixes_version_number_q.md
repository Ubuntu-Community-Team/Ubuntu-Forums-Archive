---
title: "mythtv won't autostart and -fixes version number question - WAF dropping quickly"
date: 2008-05-09
forum: Mythbuntu
---

### Post by mrand on 2008-05-09
I've had some fairly serious troubles in my upgrade from 7.10 (which was ubuntu from alt-cd + mythbuntu via apt-get) to 8.04 (which auto-upgraded me to 0.21).  But then I made the mistake of enabling -fixes, and that really broke things.  The wife acceptance factor (WAF) is dropping quickly because the system isn't really usable at this point.  The main problems I have, highest priority first:

[LIST=1]
[*]Setting up a user to auto-launch mythfrontend results in a blank screen and nothing else.  No front-end, no desktop icons or tool bar/system tray, etc.  The only thing I can see is the mythbuntu desktop logo.  I even tried creating a new user and configured it via MCC to auto-launch.  Still No dice.
[*]I can log in as a third user and launch mythfrontend manually, but the colors are super saturated.  Barely watchabble (Mostly fixed with with color/hue adjustment)
[*]My version number isn't what I expect.  I supposedly installed  0.21.0+fixes17145-0ubuntu0+mythbuntu2, but mythbackend --version shows MythTV Version: 16838 and Library API: 0.21.20080304-1
[/LIST]
There are other things on my list, but in the interest of keeping things focused, these are the ones I'd like to get resolved first.   Below is some more background and data on each of the above three items.

Could anyone shed any light on any of these three and save my Myth install?  I'm one of the types that will study things and try to figure them out on my own, but these problems have me stumped and I'm running out of free time.  I've waited until the weekend to post this so that I can be reasonably responsive to requests for more info or solution ideas.

Below are tid-bits of additional information for each of the above.  Please ask for more - I'll be happy to provide any other background info.

Thanks a million!

[INDENT]Marc[/INDENT]

---

### Post by mrand on 2008-05-09
Additional info:

(1) regarding the auto-launch error: ```
/home/guest$ less .xsession-errors
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
Agent pid 8385
/home/guest$ ps -ef | egrep guest
guest     8256     1  0 May08 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 7
guest     8258     1  0 May08 ?        00:00:00 /usr/bin/gnome-keyring-daemon -d --login
guest     8260  6914  0 May08 ?        00:00:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
guest     8353  8260  0 May08 ?        00:00:00 /usr/bin/seahorse-agent --execute /usr/share/mythbuntu/session.sh
guest     8381  8260  0 May08 ?        00:00:00 gnome-screensaver
guest     8385     1  0 May08 ?        00:00:00 /usr/bin/ssh-agent -s
guest     8390     1  0 May08 ?        00:00:00 dbus-launch --autolaunch 0c09e0fe8dbbe338bd63d800478a48c6 --binary-syntax --close-stderr
guest     8393     1  0 May08 ?        00:00:00 /usr/bin/dbus-daemon --fork --print-pid 20 --print-address 22 --session
guest     8394     1  0 May08 ?        00:00:00 /usr/bin/dbus-daemon --fork --print-pid 13 --print-address 16 --session
guest     8395     1  0 May08 ?        00:00:00 /usr/bin/dbus-launch --sh-syntax --exit-with-session
guest     8397  8260  0 May08 ?        00:00:00 /usr/bin/xfce4-session
mrand    10725 10623  0 21:04 pts/0    00:00:00 egrep guest
/home/guest$ less .dmrc

[Desktop]
Session=mythbuntu
/home/guest$
```

(2) I've gone through all the settings I can find mentioned on the mailing lists, wiki, and documentation.  Either it is something non-obvious, or I missed it somehow.

(3) extra info:
[INDENT]* Adjusted apt sources to add:
** non-free hardy items
** qbittorrent
** hardy-backports
** mythbuntu 0.21-fixes

* Did update.  A few random items updated, but connection to mythbuntu's update site wouldn't work
* A few days later, saw mythbuntu updates were available.  Clicked and found that 0.21.0+fixes17145-0ubuntu0+mythbuntu2 was available.
* Clicked install while mythbackend was recording a show.  Watched closely and saw that it shut mythbackend down as I had hoped it would
* Problem: 0.21.0+fixes17145 installed correctly as far as I could tell.  Well, except that mythbackend doesn't show it:
  $ mythbackend --version
  Please include all output in bug reports.
  MythTV Version   : 16838
  MythTV Branch    : branches/release-0-21-fixes
  Library API      : 0.21.20080304-1
  Network Protocol : 40[/INDENT]

---

### Post by prosonik on 2008-05-10
Hi there,

I'm using mythtv from the hardy repos, nothing exciting really installed.
my hardy is 32bit, upgraded first to alpha, then to release..

I'm showing the exact same version as you:

MythTV Version   : 16838
MythTV Branch    : branches/release-0-21-fixes
Library API      : 0.21.20080304-1
Network Protocol : 40

as far as the auto run issue.. I'd go the dirty way, and just stick it in:
system->preferences->session startup programs.

prosonik

---

### Post by mrand on 2008-05-10
> **prosonik said:**
> Hi there,

I'm using mythtv from the hardy repos, nothing exciting really installed.
my hardy is 32bit, upgraded first to alpha, then to release..

I'm showing the exact same version as you:

MythTV Version   : 16838
MythTV Branch    : branches/release-0-21-fixes
Library API      : 0.21.20080304-1
Network Protocol : 40

as far as the auto run issue.. I'd go the dirty way, and just stick it in:
system->preferences->session startup programs.

prosonikHowdy Prosonik,

Thanks for the reply.  Have you manually added/enabled the fixes repository (0.21 Fixes Builds) per [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)? If not, I'd kinda expect your version to be what you show above.  Does anyone know for certain they've installed 0.21.0+fixes17145?

As for autorun (I'm adding this to post 2 as well): ```
$ less .dmrc

[Desktop]
Session=mythbuntu
$
```Thanks,

[INDENT]Marc[/INDENT]

---

### Post by laga on 2008-05-10
Marc,

what does ```
apt-cache policy mythtv-frontend mythtv-backend mythtv-common libmyth-0.21-0
``` give you?

---

### Post by mrand on 2008-05-10
> **laga said:**
> Marc,

what does ```
apt-cache policy mythtv-frontend mythtv-backend mythtv-common libmyth-0.21-0
``` give you?Thanks for the reply, laga.  Here's the output

```
$ sudo apt-cache policy mythtv-frontend mythtv-backend mythtv-common libmyth-0.21-0
mythtv-frontend:
  Installed: 0.21.0+fixes17145-0ubuntu0+mythbuntu2
  Candidate: 0.21.0+fixes17145-0ubuntu0+mythbuntu2
  Version table:
 *** 0.21.0+fixes17145-0ubuntu0+mythbuntu2 0
        500 http://weeklybuilds.mythbuntu.org hardy/main Packages
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 http://us.archive.ubuntu.com hardy/multiverse Packages
     0.21.0-0ubuntu2~gutsy1 0
        500 http://us.archive.ubuntu.com gutsy-backports/multiverse Packages
mythtv-backend:
  Installed: 0.21.0+fixes17145-0ubuntu0+mythbuntu2
  Candidate: 0.21.0+fixes17145-0ubuntu0+mythbuntu2
  Version table:
 *** 0.21.0+fixes17145-0ubuntu0+mythbuntu2 0
        500 http://weeklybuilds.mythbuntu.org hardy/main Packages
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 http://us.archive.ubuntu.com hardy/multiverse Packages
     0.21.0-0ubuntu2~gutsy1 0
        500 http://us.archive.ubuntu.com gutsy-backports/multiverse Packages
mythtv-common:
  Installed: 0.21.0+fixes17145-0ubuntu0+mythbuntu2
  Candidate: 0.21.0+fixes17145-0ubuntu0+mythbuntu2
  Version table:
 *** 0.21.0+fixes17145-0ubuntu0+mythbuntu2 0
        500 http://weeklybuilds.mythbuntu.org hardy/main Packages
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 http://us.archive.ubuntu.com hardy/multiverse Packages
     0.21.0-0ubuntu2~gutsy1 0
        500 http://us.archive.ubuntu.com gutsy-backports/multiverse Packages
libmyth-0.21-0:
  Installed: 0.21.0+fixes17145-0ubuntu0+mythbuntu2
  Candidate: 0.21.0+fixes17145-0ubuntu0+mythbuntu2
  Version table:
 *** 0.21.0+fixes17145-0ubuntu0+mythbuntu2 0
        500 http://weeklybuilds.mythbuntu.org hardy/main Packages
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 http://us.archive.ubuntu.com hardy/multiverse Packages
     0.21.0-0ubuntu2~gutsy1 0
        500 http://us.archive.ubuntu.com gutsy-backports/multiverse Packages
$
```[INDENT]Marc[/INDENT]

---

### Post by mrand on 2008-05-11
Interesting datapoint: if I change the session type from Mythbuntu to Xfce, I get the same hang.  If I change it to GNOME, mythfrontend indeed comes up, although at the same time, a dialog window pops up:```

Internal error
failed to initialize Hal!
```
Looking at the .xsessions-error file: ```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/media:/tmp/.ICE-unix/6410
process 6487: arguments to dbus_connection_add_filter() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 5196.
This is normally a bug in some application using the D-Bus library.
process 6487: arguments to dbus_connection_send() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3081.
This is normally a bug in some application using the D-Bus library.
process 6487: arguments to dbus_connection_send() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3081.
This is normally a bug in some application using the D-Bus library.
process 6487: arguments to dbus_connection_send() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3081.
This is normally a bug in some application using the D-Bus library.
process 6487: arguments to dbus_connection_send() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3081.
This is normally a bug in some application using the D-Bus library.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Checking for Xgl: not present.
seahorse nautilus module initialized
Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1152x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.

(nautilus:6502): nautilus-extension-gnome-mount-WARNING **: Cannot connect to system bus: org.freedesktop.DBus.Error.NoServer : Failed to connect to
 socket /var/run/dbus/system_bus_socket: Connection refused

(nautilus:6502): nautilus-extension-gnome-mount-WARNING **: Could not initialize hal context

Connecting to system bus failed: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
ERROR: trackerd already running on your session dbus - exiting...
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2008-05-10 23:35:23.240 Using runtime prefix = /usr, libdir = /usr/lib

** (update-notifier:6583): WARNING **: hal_initialize failed: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused

system-config-printer-applet: failed to connect to system D-Bus
Window manager warning: Failed to read saved session file /home/user/.metacity/sessions/default0.ms: Failed to open file '/home/user/.metacity/sessi
ons/default0.ms': No such file or directory

** (nm-applet:6620): WARNING **: <WARN>  nma_dbus_init(): org.freedesktop.DBus.Error.NoServer raised:
 Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused



evolution-alarm-notify-Message: Setting timeout for 69877 1210550400 1210480523
evolution-alarm-notify-Message:  Sun May 11 19:00:00 2008

evolution-alarm-notify-Message:  Sat May 10 23:35:23 2008


** (gnome-panel:6501): WARNING **: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused

** (gnome-panel:6501): CRITICAL **: dbus_g_connection_get_connection: assertion `gconnection' failed
2008-05-10 23:35:23.968 XScreenSaver support enabled
2008-05-10 23:35:23.969 DPMS is active.
2008-05-10 23:35:23.969 Empty LocalHostName.
2008-05-10 23:35:23.969 Using localhost value of media
2008-05-10 23:35:23.977 New DB connection, total: 1
2008-05-10 23:35:23.981 Connected to database 'mythconverg' at host: 192.168.2.22
2008-05-10 23:35:23.982 Closing DB connection named 'DBManager0'
2008-05-10 23:35:23.983 Primary screen 0.
2008-05-10 23:35:23.984 Connected to database 'mythconverg' at host: 192.168.2.22
2008-05-10 23:35:24.007 Using screen 0, 1152x768 at 0,0

** (nautilus:6502): WARNING **: Unable to add monitor: Not supported

** (nm-applet:6620): WARNING **: <WARN>  nma_dbus_init(): org.freedesktop.DBus.Error.NoServer raised:
 Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused




** (nm-applet:6620): WARNING **: <WARN>  nma_dbus_init(): org.freedesktop.DBus.Error.NoServer raised:
 Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused




** (nm-applet:6620): WARNING **: <WARN>  nma_dbus_init(): org.freedesktop.DBus.Error.NoServer raised:
 Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused

<...last message repeated over and over forever...>
```Last datapoint: pretty much whenever it hangs at bootup, I hit <ctrl><alt><backspace> to recover from the hang, and get [INDENT]* Starting remote control daemon(s) : LIRC [fail][/INDENT] [INDENT]Marc[/INDENT]

---

### Post by mrand on 2008-05-13
After playing with the color and hue adjustements, my super saturated colors are mostly fixed.  The strange part is that this wasn't a problem on 7.10 / 0.20 - whatever the defaults were, it worked with no adjustment on my part.  Did some values automatically change on the upgrade?

As for the upgrade, version issue... I just noticed on the Mythbuntu [download page]("http://www.mythbuntu.org/downloads"), it says:> The upgrade procedure will only upgrade Mythbuntu packages if you don't have a Gnome or KDE desktop installed.This wording isn't entirely clear - does that mean the upgrade to 8.04 won't function if Gnome or KDE desktop is installed anywhere on the system?  That doesn't seem quite right.  What if you install mythbuntu on a ubuntu-desktop system (like I did)?

Lastly, is 0.21.0+fixes17145-0ubuntu0+mythbuntu2 a valid version that anyone else is running?  If so, can someone please post their --version output?

Thanks!

[INDENT]Marc[/INDENT]

---

