---
title: "No sound applications work"
date: 2011-11-01
forum: Multimedia Software
---

### Post by Affendi on 2011-11-01
I recently downgraded from 11.04 to 11.10, and now none of my sound related applications work properly if at all.  Let me break it down application by application

Audacity:
No window opens.  When run from terminal I get absolutely no response
```

$ audacity


```^my cursor sits there, no prompt. **Nothing**
However system monitor says it's running status: sleeping 
Waiting channel: poll_schedule_timeout

Amarok:
Again no window, no icon in the upper panel. 2 processes in system monitor.
When I try to run it from the shell I get this message:
```
KGlobal::locale::Warning your global KLocale is being recreated with a valid main
component instead of a fake component, this usually means you tried to call i18n related
functions before your main component was created.  You should not do that since it most
likely will not work
```Ardour:
No window, sytem monitor says it's going.  From the command line it gives what appears to be the usual start up message:
```
Ardour 2.8.11
   (built using 7387 and GCC version 4.6.1)
Copyright (C) 1999-2008 Paul Davis
Some portions Copyright (C) Steve Harris, Ari Johnson, Brett Viren, Joel Baker

Ardour comes with ABSOLUTELY NO WARRANTY
not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
This is free software, and you are welcome to redistribute it 
under certain conditions; see the source for copying conditions.
loading default ui configuration file /etc/ardour2/ardour2_ui_default.conf
loading user ui configuration file /home/michael/.ardour2/ardour2_ui.conf
Loading ui configuration file /etc/ardour2/ardour2_ui_dark.rc
theme_init() called from internal clearlooks engine
ardour: [INFO]: Ardour will be limited to 4096 open files
loading system configuration file /etc/ardour2/ardour_system.rc
loading user configuration file /home/michael/.ardour2/ardour.rc
```Avidemux:
The one and only exception.  I open it, and I get no window, just like all of the above.  Opening from the command line it says:
```
*************************
  Avidemux v2.5.4
*************************
 http://www.avidemux.org
 Code      : Mean, JSC, Grant Pedersen
 GFX       : Nestor Di, nestordi@augcyl.org
 Design    : Jakub Misak
 FreeBSD   : Anish Mistry, amistry@am-productions.biz
 Audio     : Mihail Zenkov
 Mac OS X  : Kuisathaverat, Harry van der Wolf
 Win32     : Grant Pedersen

Compiler: GCC 4.6.1
Build Target: Linux (x86)
User Interface: GTK+ (2.24.6)

Large file available: 1 offset

Initialising prefs
Directory /home/michael/.avidemux exists.Good.
Using /home/michael/.avidemux as base directory for prefs/jobs/...
Preferences found and loaded
[cpuCaps]Checking CPU capabilities
        MMX detected 
        MMXEXT detected 
        SSE detected 
        SSE2 detected 
        SSE3 detected 
        SSSE3 detected 
[cpuCaps]End of CPU capabilities check (cpuMask :ffffffff)

[SDL] Version: 1.2.14
```So I kill the process, but instead of dying it starts working.  The additional command line output that follows is a little long, so I'll won't post it unless someone requests it.

Banshee:
I see a window pop up, but then it hangs.  The terminal says this:
```
[Info  00:20:56.156] Running Banshee 2.2.0: [Ubuntu oneiric (development branch) (linux-gnu, i686) @ 2011-09-23 04:51:00 UTC]
[Info  00:20:57.215] Updating web proxy from GConf
[Info  00:20:57.412] All services are started 1.001926
** (Banshee:6041): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:6041): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'
[Info  00:20:57.868] Querying MusicBrainz for Disc Release (jYie.gNGe2eico92xiWsDADuE2Q-)
[Info  00:20:57.903] AmazonMP3 store redirect URL: https://one.ubuntu.com/music/store/amz/
[Info  00:20:58.243] nereid Client Started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```If I kill it, and then start up jackd (see below), and then try again it says the same thing with the addition of one line:
```
[Info  00:20:59.126] Query finished (success: False, 1.257615 seconds)
```gnome alsa mixer:
No window.  Terminal:
```
(gnome-alsamixer:6104): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-alsamixer:6104): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-alsamixer:6104): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:6104): Gtk-CRITICAL **: IA__gtk_icon_theme_has_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed

(gnome-alsamixer:6104): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed

(gnome-alsamixer:6104): GLib-CRITICAL **: g_hash_table_insert_internal: assertion `hash_table != NULL' failed

(gnome-alsamixer:6104): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:6104): Gtk-CRITICAL **: IA__gtk_icon_theme_has_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed

(gnome-alsamixer:6104): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:6104): Gtk-CRITICAL **: IA__gtk_icon_theme_has_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed

(gnome-alsamixer:6104): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:6104): Gtk-CRITICAL **: IA__gtk_icon_theme_has_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed
```Pulse Audio Volume Control:
A window appears.  It says "Establishing connection to PulseAudio.  Please wait..."  It does not hang, I can close it without killing the process.  No output from the terminal.  It was like this before I downgraded.

It's getting late for me, so I'll finish posting application breakdown tomorrow.
But before I go...
DO NOT:
-Tell me to reinstall pulseaudio, gstreamer, or alsa
-Tell me to make sure the volume is turned up in alsa mixer (which seems to be working)
-Tell me to make sure I have the right sound card selected in alsamixer

I already tried that.
Oh and my browser hangs whenever I try to run any sort of flash content.  Don't tell me to install the latest flash plugin manually (i.e. download the .so and then move to plugin directory), I tried that already.

---

### Post by Gaygerbil on 2011-11-01
Same issue for me it's Gnome Alsa-mixer that no longer works.

---

### Post by Affendi on 2011-11-05
Is that the only application that doesn't work for you?

---

### Post by Affendi on 2011-11-05
Ok, and the rest...

QJackCtl:
I get a window but there's nothing in it, the title reads "JACK Audio Connection Kit [(default)] Inactive." The terminal says: "Warning: no translation found for 'en_US' locale: /usr/share/qt4/translations/qt_en_US.qm
Warning: no translation found for 'en_US' locale: /usr/share/locale/qjackctl_en_US.qm
"
When I run jackd it displays the typical start up message.
Any program powered by JACK behaves the same as qjackctl, it starts and then hangs.

I've tried running flash on all browsers I have, Chromium, Firefox, Seamonkey, and Rekonq, none of them works.

Is this problem fixable?  I have the feeling that some Lovecraftian horror is behind this.

---

### Post by Affendi on 2011-11-05
If Gnome alsamixer doesn't work for you you can just run 'alsamixer' from the terminal, even that works for me.

---

### Post by Gaygerbil on 2011-11-08
Yea the terminal Alsamixer works for me as well but that's different than Gnome-Alsamixer I believe. 

When I run Gnome-Alsamixer I get this error in the terminal:

```
(gnome-alsamixer:8956): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed
Segmentation fault
```

---

### Post by Affendi on 2011-11-08
I think you have a different problem, gnome-alsamixer doesn't appear to be working for a lot of people.  But good luck with that.  I'm starting to think I should submit a bug report, but I feel like I should find more out about my problem, do more diagnostic tests first.

---

