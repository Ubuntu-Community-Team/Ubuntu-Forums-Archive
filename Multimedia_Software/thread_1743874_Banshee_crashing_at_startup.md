---
title: "Banshee crashing at startup"
date: 2011-04-29
forum: Multimedia Software
---

### Post by TaffyDownUnder on 2011-04-29
Hi,
just upgraded from 10.10 to 11.04 (64-bit). When I run banshee it appears for a second and then disappears. Running from a terminal produces the following:

[Info  11:59:46.668] Running Banshee 2.0.0: [Ubuntu Natty (development branch) (linux-gnu, x86_64) @ 2011-04-18 16:18:52 UTC]
[Info  11:59:47.987] Updating web proxy from GConf
[Info  11:59:48.076] All services are started 1.164777
** (Banshee:3762): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:3762): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'
** (Banshee:3762): DEBUG: Loading the real store page

** (Banshee:3762): WARNING **: Got less number of items in credentials hash table than expected!
[Info  11:59:49.215] nereid Client Started
[Info  11:59:49.310] GStreamer version 0.10.32.0, gapless: True, replaygain: False
[Info  11:59:49.469] AppleDeviceSource is ignoring unmounted volume SecureDocs
[Info  11:59:49.498] AppleDeviceSource is ignoring unmounted volume Media
[Info  11:59:49.499] AppleDeviceSource is ignoring unmounted volume Documents
[Info  11:59:49.500] AppleDeviceSource is ignoring unmounted volume SharedDocs

Unhandled Exception: GLib.GException: Can't recursively copy directory
  at GLib.FileAdapter.Move (File destination, FileCopyFlags flags, GLib.Cancellable cancellable, GLib.FileProgressCallback progress_callback) [0x00000] in <filename unknown>:0 
  at Banshee.IO.Gio.Directory.Move (Hyena.SafeUri from, Hyena.SafeUri to) [0x00000] in <filename unknown>:0 
  at Banshee.IO.Directory.Move (Hyena.SafeUri from, Hyena.SafeUri to) [0x00000] in <filename unknown>:0 
  at Banshee.Podcasting.PodcastService.<DelayedInitialize>m__11 () [0x00000] in <filename unknown>:0 

My music is stored on a mounted network drive with a symlink from Music to the appropriate directory on the mounted drive.  Despite what the messages say above all volumes are mounted.

---

### Post by greenjumper on 2011-05-03
Same problem here!

---

### Post by mörgæs on 2011-05-04
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

