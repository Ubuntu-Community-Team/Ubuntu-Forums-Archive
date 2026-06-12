---
title: "Banshee exits when I click smart playlist"
date: 2010-07-15
forum: Multimedia Software
---

### Post by Adbekunkus on 2010-07-15
Hi. I use banshee and have a smart playlist for each of the genres of music I have, and this thig keeps happening whenever I click on one of them: banshee just exits. I ran it on a terminal and this is the output:
oscar@laptpo:~$ banshee
[Info  19:22:11.692] Running Banshee 1.6.1: [Ubuntu 9.10 (linux-gnu, i486) @ 2010-05-27 14:21:52 UTC]

(/usr/lib/banshee-1/Banshee.exe:3724): GLib-WARNING **: g_set_prgname() called multiple times
[Info  19:22:13.297] All services are started 1.289466
[Info  19:22:16.170] nereid Client Started
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
Mono.Data.Sqlite.SqliteException: The database disk image is malformed
database disk image is malformed
  at Mono.Data.Sqlite.Sqlite3.Reset (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] 
  at Mono.Data.Sqlite.Sqlite3.Step (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] 
  at Mono.Data.Sqlite.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Data.Sqlite.SqliteCommand:ExecuteNonQuery ()
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.Sqlite.SqliteConnection connection) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.buttonpressevent_cb(IntPtr widget, IntPtr evnt)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Banshee.Gui.GtkBaseClient.Run()
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
   at Nereid.Client.Main(System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()
 

Can anyone tell me what's wrong with my banshee? I'm using Karmic, I'm a rookie in all matters concerning Ubuntu and I'd like to keep using banshee. Thanks

---

