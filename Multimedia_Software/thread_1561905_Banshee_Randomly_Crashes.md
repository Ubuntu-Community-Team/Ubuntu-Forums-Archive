---
title: "Banshee Randomly Crashes"
date: 2010-08-26
forum: Multimedia Software
---

### Post by Nostigex on 2010-08-26
Banshee crashes (or exits out) every so often when switching between tracks. Firefox does the same thing, although less often, usually when clicking on links. Don't know if they're related. What other information can I provide that would help diagnose the problem, and how do I collect it? OR... what's the problem?

---

### Post by Nostigex on 2010-08-27
bump

---

### Post by Joseph Schwenker on 2011-07-31
I experience the same problem. Here's the output:

```
[Info  17:39:29.967] Running Banshee 1.8.1: [Ubuntu 10.10 (linux-gnu, i686) @ 2011-02-02 09:04:16 UTC]
[Info  17:39:30.674] Starting collection of anonymous usage data
[Info  17:39:31.678] Updating web proxy from GConf
[Info  17:39:31.729] All services are started 1.308878

(Banshee:3192): IBUS-WARNING **: Connect to unix:abstract=/tmp/dbus-MOdh8tSM5N,guid=1c757efb5fcaec926dc7c86300000040 failed: Failed to connect to socket /tmp/dbus-MOdh8tSM5N: Connection refused.
[Warn  17:39:31.879] Forcefully breaking out of RCS loop b/c change in total_width less than 1.0
[Warn  17:39:32.534] Forcefully breaking out of RCS loop b/c change in total_width less than 1.0
[Info  17:39:32.600] nereid Client Started
[Info  17:39:34.162] Uncached artwork size 183 requested
[Info  17:44:50.062] Uncached artwork size 183 requested
[Info  17:51:09.063] Uncached artwork size 183 requested
[Info  17:54:11.215] Uncached artwork size 183 requested
[Info  18:07:41.210] Uncached artwork size 183 requested
[Info  18:11:36.024] Uncached artwork size 183 requested
[Info  18:27:30.589] Uncached artwork size 183 requested
[Info  18:32:28.859] Uncached artwork size 183 requested
[Info  18:35:02.937] Uncached artwork size 183 requested

Unhandled Exception: System.FormatException: Input string was not in the correct format
at int.Parse (string,System.Globalization.NumberStyles,System.IFormatProvider) <0x00046>
at int.Parse (string,System.IFormatProvider) <0x00015>
at System.Convert.ToInt32 (string,System.IFormatProvider) <0x0001d>
at string.System.IConvertible.ToInt32 (System.IFormatProvider) <0x00013>
at Banshee.Collection.Database.DatabaseTrackListModel.Reload (Hyena.Data.IListModel) <0x002e6>
at Banshee.Collection.Database.DatabaseTrackListModel.Reload () <0x00012>
at Banshee.Sources.DatabaseSource.RateLimitedReload () <0x00036>
at Banshee.Base.RateLimiter.InnerExecute () <0x0004e>
at Banshee.Base.RateLimiter.Execute () <0x00060>
at Banshee.Sources.DatabaseSource.Reload () <0x00027>
at Banshee.SmartPlaylist.SmartPlaylistSource.Reload () <0x0005a>
at Banshee.SmartPlaylist.SmartPlaylistSource.RefreshAndReload () <0x00027>
at Banshee.SmartPlaylist.SmartPlaylistSource.HandleTracksChanged (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs) <0x000ee>
at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler.invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs) <0x00046>
at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler.invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs) <0x00075>
at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler.invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs) <0x00075>
at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler.invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs) <0x00075>
at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler.invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs) <0x00075>
at (wrapper delegate-invoke) Banshee.Sources.PrimarySource/TrackEventHandler.invoke_void__this___Source_TrackEventArgs (Banshee.Sources.Source,Banshee.Sources.TrackEventArgs) <0x00075>
at Banshee.Sources.PrimarySource/<OnTracksChanged>c__AnonStorey19.<>m__13 () <0x000ab>
at Hyena.ThreadAssist.SpawnFromMain (System.Threading.ThreadStart) <0x0002f>
at Banshee.Sources.PrimarySource.OnTracksChanged (Hyena.Query.QueryField[]) <0x00058>
at Banshee.Sources.PrimarySource.NotifyTracksChanged (Hyena.Query.QueryField[]) <0x0001c>
at Banshee.Collection.Database.DatabaseTrackInfo.Save (bool,Hyena.Query.QueryField[]) <0x00257>
at Banshee.Collection.Database.DatabaseTrackInfo.UpdateLastPlayed () <0x0006f>
at Banshee.GStreamer.PlayerEngine.OnAboutToFinish (intptr) <0x0001b>
at (wrapper native-to-managed) Banshee.GStreamer.PlayerEngine.OnAboutToFinish (intptr) <0x00054>
```

---

