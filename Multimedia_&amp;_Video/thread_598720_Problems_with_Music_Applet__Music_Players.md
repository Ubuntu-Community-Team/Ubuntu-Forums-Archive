---
title: "Problems with Music Applet / Music Players"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by galvao on 2007-10-31
Greetings.

Gutsy here.

I'm having several issues involving Gnome's Music Applet and several Music Players. There a lot of problems that probably have several causes, so I'll try to describe everything in detail:

1) I personally love Banshee, but it's been crashing a lot on me. I have a somewhat big play list (around 9GB, 2,500 files) and when I try to remove the entire Library, so I can add the whole thing again***** it ends up crashing.

*** **Is there an easier way of making Banshee "watch" a folder for new files and automatically update it's Music Library?

2) I tried then to make XMMS, XMMS2 and BMP to work:
 - XMMS seems to work fine, but I can't enable it in the Music Applet (tells me that there is no module named xmms.control, although I installed every package related to it.
- XMMS2 Don't even appear on the "Sound & Video" menu, aside from not being able to enable it in Music Applet for the exact same reason ("No module named xmmsclient)
- BMP (Beep Media Player) works great when I start it from the "Sound & Video" Menu, but it doesn't show at all at Music Applet, is this "normal"?

So, this post might sound a little confusing and I'm sorry for that, so let me list my problems priorities:

1) To solve Banshee's problem, if possible
2) To make BMP, XMMS2 or XMMS to work with the Music Applet

***UPDATE: Here's the complete Banshee output, when running from the shell, untill the point it dies

galvao@galvao-desktop ~> banshee
Debug: [10/31/2007 6:40:56 PM] (Loading audio profiles) - /usr/share/banshee/audio-profiles
Debug: [10/31/2007 6:40:57 PM] (Default player engine) - GStreamer 0.10
Debug: [10/31/2007 6:40:57 PM] (Audio CD Core Initialized) - 
Debug: [10/31/2007 6:40:57 PM] (Testing device for DAP support) - /org/freedesktop/Hal/devices/volume_uuid_1356785047E60361
Debug: [10/31/2007 6:40:57 PM] (DAP has not been added) - /org/freedesktop/Hal/devices/volume_uuid_1356785047E60361
Warning: [10/31/2007 6:40:57 PM] (Power Management Call Failed) - Cannot find GNOME Power Manager: Name org.gnome.PowerManager has no owner
Debug: [10/31/2007 6:40:57 PM] (Enabled multimedia keys support) - Using org.gnome.SettingsDaemon
Debug: [10/31/2007 6:40:57 PM] (Audioscrobbler starting protocol engine) - 
Building initial DAAP database from local library...
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
Mono.Data.SqliteClient.SqliteSyntaxException: Expression tree is too large (maximum depth 1000)
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 

   at GLib.ExceptionManager.RaiseUnhandledException ()
   at GLib.Signal.voidObjectCallback ()
   at GLib.Signal.voidObjectCallback ()
   at Gtk.Application.gtk_main ()
   at Gtk.Application.gtk_main ()
   at Gtk.Application.Run ()
   at Gnome.Program.Run ()
   at Banshee.BansheeEntry.Startup ()
   at System.MulticastDelegate.invoke_void_string[] ()
   at Banshee.Gui.CleanRoomStartup.Startup ()
   at Banshee.BansheeEntry.Main ()
fish: Job 1, &#8220;banshee&#8221; terminated by signal Unknown (Unknown)

Thank you all in advance,

---

### Post by Alexandre_Joker on 2007-12-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/music-applet/+bug/139447](https://bugs.launchpad.net/ubuntu/+source/music-applet/+bug/139447) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hey, man!...
I've just installed the package named "python-xmms" from the synaptic package manager and then... xmms module got ready! Ok, ok, I'm still in feisty because problems with my usb wireless card and its driver rt2570, but you can try the same procedure!... Oh, about Banshee, I don't have your answer.
Good luck!...:)

---

### Post by Supreme1012 on 2008-03-08
thanks for the post! going into synaptic and installing python-xmms makes the plugin for xmms work.

---

