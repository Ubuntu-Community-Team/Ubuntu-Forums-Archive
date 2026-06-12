---
title: "Banshee crashes on startup"
date: 2011-08-19
forum: Multimedia Software
---

### Post by cidthecoatrack on 2011-08-19
Hi everyone. I'm fairly new to linux, but the forums have been a great help in getting myself adjusted. :)

I am creating a media computer, one to hold all my video, music, etc.  Therefore, the most important program to run is Banshee (by my own choice of media players).  However, recently, Banshee has taken to crashing within a few seconds of the program loading.  At one point, I logged out and logged back in, and the program worked wonderfully, but I have not been able to reproduce that.  So far, it does not run.  Here is what I get from the terminal:


[Info  17:29:14.806] Running Banshee 2.0.1: [Ubuntu 11.04 (linux-gnu, x86_64) @ 2011-07-03 20:56:56 UTC]
/usr/share/themes/Kiwi/gtk-2.0/gtkrc:78: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Kiwi/gtk-2.0/gtkrc:82: Murrine configuration option "gradients" is no longer supported and will be ignored.
[Warn  17:29:17.219] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  17:29:17.219] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  17:29:17.236] Updating web proxy from GConf
[Warn  17:29:17.320] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  17:29:17.320] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  17:29:17.322] All services are started 2.103299
[Info  17:29:27.916] nereid Client Started
[Info  17:29:28.059] GStreamer version 0.10.32.0, gapless: False, replaygain: False

Unhandled Exception: System.OverflowException: Value is greater than Int32.MaxValue or less than Int32.MinValue
  at System.Convert.ToInt32 (Int64 value) [0x00000] in <filename unknown>:0 
  at System.Int64.System.IConvertible.ToInt32 (IFormatProvider provider) [0x00000] in <filename unknown>:0 
  at System.Convert.ToInt32 (System.Object value, IFormatProvider provider) [0x00000] in <filename unknown>:0 
  at System.Convert.ToInt32 (System.Object value) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteConnection.Execute (Hyena.Data.Sqlite.HyenaSqliteCommand command) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteConnection.Execute (System.String command_str, System.Object[] param_values) [0x00000] in <filename unknown>:0 
  at Banshee.SmartPlaylist.SmartPlaylistSource.Refresh () [0x00000] in <filename unknown>:0 
  at Banshee.SmartPlaylist.SmartPlaylistSource.RefreshAndReload () [0x00000] in <filename unknown>:0 
  at Banshee.SmartPlaylist.SmartPlaylistSource.HandleTracksChanged (Banshee.Sources.Source sender, Banshee.Sources.TrackEventArgs args) [0x00000] in <filename unknown>:0 
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler:invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs)
  at Banshee.Sources.PrimarySource+<OnTracksChanged>c__AnonStorey21.<>m__18 () [0x00000] in <filename unknown>:0 
  at Hyena.ThreadAssist.SpawnFromMain (System.Threading.ThreadStart threadedMethod) [0x00000] in <filename unknown>:0 
  at Banshee.Sources.PrimarySource.OnTracksChanged (Hyena.Query.QueryField[] fields) [0x00000] in <filename unknown>:0 
  at Banshee.Sources.DatabaseSource.OnTracksChanged () [0x00000] in <filename unknown>:0 
  at Banshee.Sources.PrimarySource.NotifyTracksChanged () [0x00000] in <filename unknown>:0 
  at Banshee.LibraryWatcher.SourceWatcher.Watch () [0x00000] in <filename unknown>:0 

Obviously, something's wrong in how it's reading the smart playlists.  I tried simply repairing the library using sqlite3 and such, but that did not fix it.  I am running xubuntu on a 64-bit machine (AMD Athlon 64).  The only other thing I can think to note is that I was recently trying to sync my iPod, and the crashing has occurred since ejecting the iPod.  Plugging the iPod back in has also not remedied the situation.

Any help you can offer is greatly appreciated.  Thanks in advance!

---

### Post by teledyn on 2012-05-31
I began seeing the very same behaviour this morning, did a reboot in case there were overnight lib updates but the issue persists; it will sometimes play just one song before it collapses with the OverflowException

this is ubuntu 11.10 on i386

as with Cid, my use-case is a media server where Banshee powers the home FM-transmitter and it is important that the screen always show the track now playing -- I'll gladly switch back to Rhythmbox if someone can point me at an equivalent function to Banshee's Now Playing + Fullscreen

---

### Post by teledyn on 2012-05-31
I removed the .cache/banshee-1 and .config/banshee-1 directories and so far so good.  It had to rebuild the db, but I reasoned that the backtrace leads into the persistence layer libraries so perhaps something was changed in the db format.

---

