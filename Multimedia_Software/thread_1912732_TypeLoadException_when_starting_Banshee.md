---
title: "TypeLoadException when starting Banshee"
date: 2012-01-21
forum: Multimedia Software
---

### Post by rbretherton on 2012-01-21
Hi Folks,

When I try to run Banshee, the window appears, but then disappears. Running Banshee from the command line gives this output:

```

$ banshee -debug
[Info  12:00:31.018] Running Banshee 2.2.1: [Ubuntu 11.10 (linux-gnu, x86_64) @ 2011-12-19 14:58:04 UTC]
[Info  12:00:32.160] Updating web proxy from GConf
[Info  12:00:32.200] All services are started 0.65131
** (Banshee:3940): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:3940): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'

(Banshee:3940): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
[Info  12:00:32.637] AmazonMP3 store redirect URL: https://one.ubuntu.com/music/store/amz/
** (Banshee:3940): DEBUG: Loading the real store page

** (Banshee:3940): WARNING **: Got less number of items in credentials hash table than expected!
[Info  12:00:33.312] nereid Client Started
[Info  12:00:33.386] GStreamer version 0.10.35.0, gapless: True, replaygain: False

Unhandled Exception: System.TypeLoadException: A type load exception has occurred.
  at System.Threading.Thread.StartUnsafe () [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeLoadException: A type load exception has occurred.
  at System.Threading.Thread.StartUnsafe () [0x00000] in <filename unknown>:0 

```

Banshee has worked for me in the past, but I don't know what change has caused this error. I have tried deleting the ~/.config/banshee-1 directory and reinstalling Banshee, but neither made any difference.

Any ideas?


Thanks,


Richard

---

### Post by rbretherton on 2012-01-28
For anyone interested the Banshee mailing list suggested I raise this as a bug. The report is here:
[https://bugzilla.gnome.org/show_bug.cgi?id=668892](https://bugzilla.gnome.org/show_bug.cgi?id=668892)

Thanks

---

