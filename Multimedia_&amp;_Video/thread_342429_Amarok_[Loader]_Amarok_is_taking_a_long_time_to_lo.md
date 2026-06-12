---
title: "Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wro"
date: 2007-01-20
forum: Multimedia &amp; Video
---

### Post by fakie_flip on 2007-01-20
I tried to play a mp3 in Amarok. Amarok said there was no mp3 support and would I like to add it, so I told it to add mp3 support and it asked for my password. After a little bit, Amarok would not play a mp3, so I thought, maybe I need to restart Amarok for it to be able to play a mp3 just like Firefox has to be restarted for new plugins to work. It showed the blue box that it normally does when it is starting except it stayed there for a while and then went away. I could not use Amarok, and it was not showing in the gnome panel. I could not start Amarok because ps showed that it was already running, so I killed all instances of it and tried to run it in terminal. The blue box showed, but when it went away it gave me the last message about something being wrong with Amarok. I have tried removing and purging amarok, amarok-xine, and libxine-extracodecs. Then I installed amarok and amarok-xine again, but the same problem. I choose to reinstall those packages because the /var/log/dpkg.log showed said they half installed and half configured. Does this mean I have to reinstall Ubuntu again if I want Amarok to work? :( 

```
chris@ubuntu:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?

```

```
2007-01-20 00:06:29 install libmad0 <none> 0.15.1b-2.1
2007-01-20 00:06:29 status half-installed libmad0 0.15.1b-2.1
2007-01-20 00:06:29 status unpacked libmad0 0.15.1b-2.1
2007-01-20 00:06:29 status unpacked libmad0 0.15.1b-2.1
2007-01-20 00:06:29 install libxine-extracodecs <none> 1.1.2-0ubuntu2
2007-01-20 00:06:29 status half-installed libxine-extracodecs 1.1.2-0ubuntu2
2007-01-20 00:06:30 status unpacked libxine-extracodecs 1.1.2-0ubuntu2
2007-01-20 00:06:30 status unpacked libxine-extracodecs 1.1.2-0ubuntu2
2007-01-20 00:06:30 status unpacked libmad0 0.15.1b-2.1
2007-01-20 00:06:30 status half-configured libmad0 0.15.1b-2.1
2007-01-20 00:06:32 status installed libmad0 0.15.1b-2.1
2007-01-20 00:06:32 status unpacked  1.1.2-0ubuntu2
2007-01-20 00:06:32 status half-configured libxine-extracodecs 1.1.2-0ubuntu2
2007-01-20 00:06:32 status installed libxine-extracodecs 1.1.2-0ubuntu2
2007-01-20 00:11:37 status installed amarok 2:1.4.3-0ubuntu10
2007-01-20 00:11:37 status installed amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:11:37 status installed amarok 2:1.4.3-0ubuntu10
2007-01-20 00:11:37 status installed amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:11:37 status installed amarok 2:1.4.3-0ubuntu10
2007-01-20 00:11:37 status installed amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:11:37 status installed amarok 2:1.4.3-0ubuntu10
2007-01-20 00:11:37 status installed amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:11:37 status installed amarok 2:1.4.3-0ubuntu10
2007-01-20 00:11:37 status installed amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:11:37 status installed amarok 2:1.4.3-0ubuntu10
2007-01-20 00:11:37 status installed amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:11:37 status installed amarok 2:1.4.3-0ubuntu10
2007-01-20 00:43:45 remove libxine-extracodecs 1.1.2-0ubuntu2 1.1.2-0ubuntu2
2007-01-20 00:43:45 status half-configured libxine-extracodecs 1.1.2-0ubuntu2
2007-01-20 00:43:45 status half-installed libxine-extracodecs 1.1.2-0ubuntu2
2007-01-20 00:43:45 status config-files libxine-extracodecs 1.1.2-0ubuntu2
2007-01-20 00:43:45 status config-files libxine-extracodecs 1.1.2-0ubuntu2
2007-01-20 00:43:45 status config-files libxine-extracodecs 1.1.2-0ubuntu2
2007-01-20 00:43:45 status not-installed libxine-extracodecs <none>
2007-01-20 00:44:00 status installed libmad0 0.15.1b-2.1
2007-01-20 00:44:00 remove libmad0 0.15.1b-2.1 0.15.1b-2.1
2007-01-20 00:44:00 status half-configured libmad0 0.15.1b-2.1
2007-01-20 00:44:00 status half-installed libmad0 0.15.1b-2.1
2007-01-20 00:44:00 status config-files libmad0 0.15.1b-2.1
2007-01-20 00:44:00 purge libmad0 0.15.1b-2.1 0.15.1b-2.1
2007-01-20 00:44:00 status config-files libmad0 0.15.1b-2.1
2007-01-20 00:44:00 status config-files libmad0 0.15.1b-2.1
2007-01-20 00:44:00 status config-files libmad0 0.15.1b-2.1
2007-01-20 00:44:00 status config-files libmad0 0.15.1b-2.1
2007-01-20 00:44:03 status config-files libmad0 0.15.1b-2.1
2007-01-20 00:44:03 status not-installed libmad0 <none>
2007-01-20 00:44:23 status installed amarok 2:1.4.3-0ubuntu10
2007-01-20 00:44:23 status installed amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:44:23 status installed amarok 2:1.4.3-0ubuntu10
2007-01-20 00:44:23 status installed amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:44:23 status installed amarok 2:1.4.3-0ubuntu10
2007-01-20 00:44:23 status installed amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:44:23 status installed amarok 2:1.4.3-0ubuntu10
2007-01-20 00:44:23 status installed amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:44:23 status installed amarok 2:1.4.3-0ubuntu10
2007-01-20 00:44:23 status installed amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:44:23 status installed amarok 2:1.4.3-0ubuntu10
2007-01-20 00:44:23 status installed amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:44:23 status installed amarok 2:1.4.3-0ubuntu10
2007-01-20 00:44:23 remove amarok 2:1.4.3-0ubuntu10 2:1.4.3-0ubuntu10
2007-01-20 00:44:23 status half-configured amarok 2:1.4.3-0ubuntu10
2007-01-20 00:44:23 status half-installed amarok 2:1.4.3-0ubuntu10
2007-01-20 00:44:24 status config-files amarok 2:1.4.3-0ubuntu10
2007-01-20 00:44:24 purge amarok 2:1.4.3-0ubuntu10 2:1.4.3-0ubuntu10
2007-01-20 00:44:24 status config-files amarok 2:1.4.3-0ubuntu10
2007-01-20 00:44:24 status config-files amarok 2:1.4.3-0ubuntu10
2007-01-20 00:44:24 status config-files amarok 2:1.4.3-0ubuntu10
2007-01-20 00:44:24 status config-files amarok 2:1.4.3-0ubuntu10
2007-01-20 00:44:24 status config-files amarok 2:1.4.3-0ubuntu10
2007-01-20 00:44:24 status not-installed amarok <none>
2007-01-20 00:44:24 status installed amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:44:24 remove amarok-xine 2:1.4.3-0ubuntu10 2:1.4.3-0ubuntu10
2007-01-20 00:44:24 status half-configured amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:44:24 status half-installed amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:44:24 status config-files amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:44:24 status config-files amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:44:24 status config-files amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:44:24 status not-installed amarok-xine <none>
2007-01-20 00:46:22 install amarok-xine <none> 2:1.4.3-0ubuntu10
2007-01-20 00:46:22 status half-installed amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:46:22 status unpacked amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:46:22 status unpacked amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:46:22 install amarok <none> 2:1.4.3-0ubuntu10
2007-01-20 00:46:22 status half-installed amarok 2:1.4.3-0ubuntu10
2007-01-20 00:46:23 status unpacked amarok 2:1.4.3-0ubuntu10
2007-01-20 00:46:23 status unpacked amarok 2:1.4.3-0ubuntu10
2007-01-20 00:46:23 install libmad0 <none> 0.15.1b-2.1
2007-01-20 00:46:23 status half-installed libmad0 0.15.1b-2.1
2007-01-20 00:46:23 status unpacked libmad0 0.15.1b-2.1
2007-01-20 00:46:24 status unpacked libmad0 0.15.1b-2.1
2007-01-20 00:46:24 install libxine-extracodecs <none> 1.1.2-0ubuntu2
2007-01-20 00:46:24 status half-installed libxine-extracodecs 1.1.2-0ubuntu2
2007-01-20 00:46:24 status unpacked libxine-extracodecs 1.1.2-0ubuntu2
2007-01-20 00:46:24 status unpacked libxine-extracodecs 1.1.2-0ubuntu2
2007-01-20 00:46:24 status unpacked libmad0 0.15.1b-2.1
2007-01-20 00:46:24 status half-configured libmad0 0.15.1b-2.1
2007-01-20 00:46:24 status installed libmad0 0.15.1b-2.1
2007-01-20 00:46:24 status unpacked libxine-extracodecs 1.1.2-0ubuntu2
2007-01-20 00:46:24 status half-configured libxine-extracodecs 1.1.2-0ubuntu2
2007-01-20 00:46:24 status installed libxine-extracodecs 1.1.2-0ubuntu2
2007-01-20 00:46:24 status unpacked amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:46:24 status half-configured amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:46:24 status installed amarok-xine 2:1.4.3-0ubuntu10
2007-01-20 00:46:24 status unpacked amarok 2:1.4.3-0ubuntu10
2007-01-20 00:46:24 status unpacked amarok 2:1.4.3-0ubuntu10
2007-01-20 00:46:24 status half-configured amarok 2:1.4.3-0ubuntu10
2007-01-20 00:46:24 status installed a
```

---

### Post by Servechilled on 2008-03-12
I'm having the same problem, though I haven't tried reinstalling Amarok. Here's my terminal output:

```

chris@chris-desktop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x81526d0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x81526d0 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?

```

Running xine-check I get this output:
```

chris@chris-desktop:~$ xine-check
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.22-14-rt)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ good ] found the player at /usr/bin/xine
[ good ] /usr/bin/xine is in your PATH
[ hint ] No xine-config found. Assuming xine from Debian package
         The xine-config script can be used to determine some file locations
         used by xine-lib, but you don't have such a script on your system.
         However, it looks like you installed xine from the Debian packages.
         So I'll just guess that you are using the standard locations.
         If you want me to be sure about those file locations, you can install
         the 'libxine-dev' package, which contains xine-config. However, this
         package is not really needed to run xine...
         press <enter> to continue...

[ good ] plugin directory /usr/lib/xine/plugins exists.
[OUCH!!] There are no input plugins.
         xine needs at least one input plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no demux plugins.
         xine needs at least one demux plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no decoder plugins.
         xine needs at least one decoder plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no video_out plugins.
         xine needs at least one video_out plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no audio_out plugins.
         xine needs at least one audio_out plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/hda
[ good ] /dev/dvd points to /dev/hda
[ good ] DMA is enabled for your DVD drive
[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  YUY2 YV12 UYVY I420 YUY2 YV12 UYVY I420

```

So I installed libxine-dev and got this from amarok's output:
```

chris@chris-desktop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/mb-applet-clock.desktop has Type=PanelApp instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/mb-applet-clock.desktop
kio (KService*): WARNING: The desktop entry file /usr/share/applications/mb-applet-system-monitor.desktop has Type=PanelApp instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/mb-applet-system-monitor.desktop
kio (KService*): WARNING: The desktop entry file /usr/share/applications/mb-applet-menu-launcher.desktop has Type=PanelApp instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/mb-applet-menu-launcher.desktop
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x815a2a8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x815a2a8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?

```

edit:: Oh, this thread is a year old. I just realized that. Still any help is appreciated.
edit 2: different amarok output due to reinstalling xine-ui and installiing libxine-dev
edit 3: Running amarok as root ($ sudo amarok) works perfect.

---

