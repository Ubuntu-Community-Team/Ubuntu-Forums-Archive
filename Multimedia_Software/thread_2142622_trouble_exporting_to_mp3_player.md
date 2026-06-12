---
title: "trouble exporting to mp3 player"
date: 2013-05-06
forum: Multimedia Software
---

### Post by rumney8 on 2013-05-06
could somebody help me please.
Im trying too put songs on to a media player using banshee, it will put songs on that are already mp3 format but when it trys to convert the .m4a songs it crashes i've downloaded all the gstreamer codecs.

here the error it comes up with 

An unhandled exception was thrown: Object reference not set to an instance of an object


at Banshee.Sources.PrimarySource.IncrementAddedTracks () <0x0004d>
at Banshee.Dap.DapSource.OnTrackTranscodeError (Banshee.Collection.TrackInfo) <0x00067>
at Banshee.MediaEngine.TranscoderService.OnError (object,Banshee.MediaEngine.TranscoderErrorArgs) <0x0007c>
at Banshee.GStreamer.Transcoder.OnError (Banshee.Collection.TrackInfo,string) <0x00063>
at Banshee.GStreamer.Transcoder.OnNativeError (intptr,intptr,intptr) <0x000f4>
at (wrapper native-to-managed) Banshee.GStreamer.Transcoder.OnNativeError (intptr,intptr,intptr) <0x00083>
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00054>
at Gtk.Application.Run () <0x0000b>
at Banshee.Gui.GtkBaseClient.Run () <0x0005f>
at Banshee.Gui.GtkBaseClient.Startup () <0x00049>
at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x0008e>




.NET Version: 4.0.30319.1
OS Version: Unix 3.8.0.19


Assembly Version Information:


taglib-sharp (2.1.0.0)
Mono.Security (4.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mtp (2.6.0.0)
libgpod-sharp (1.1.0.0)
Banshee.Dap.AppleDevice (2.6.0.0)
Banshee.Dap.Mtp (2.6.0.0)
Banshee.Dap.MassStorage (2.6.0.0)
Mono.Zeroconf.Providers.AvahiDBus (4.0.0.90)
Mono.Zeroconf (4.0.0.90)
Banshee.PlayQueue (2.6.0.0)
Banshee.InternetRadio (2.6.0.0)
Banshee.LiveRadio (2.4.0.0)
Banshee.WebBrowser (2.6.0.0)
Banshee.MiroGuide (2.6.0.0)
Banshee.FileSystemQueue (2.6.0.0)
Banshee.MultimediaKeys (2.6.0.0)
Banshee.LibraryWatcher (2.6.0.0)
gkeyfile-sharp (1.0.0.0)
Banshee.OpticalDisc (2.6.0.0)
notify-sharp (0.4.0.0)
Banshee.SoundMenu (2.6.0.0)
Banshee.Dap (2.6.0.0)
Banshee.Mpris (2.6.0.0)
Banshee.CoverArt (2.6.0.0)
Banshee.AlbumArtWriter (2.4.0.0)
Banshee.CoverWallpaper (2.4.0.0)
Banshee.Daap (2.6.0.0)
Migo (2.6.0.0)
Banshee.Podcasting (2.6.0.0)
pango-sharp (2.12.0.0)
Mono.Cairo (4.0.0.0)
Banshee.Fixup (2.6.0.0)
Banshee.Widgets (2.6.0.0)
gio-sharp (2.14.0.0)
gudev-sharp (1.0.0.0)
Banshee.Gio (2.6.0.0)
Banshee.GStreamer (2.6.0.0)
System.Configuration (4.0.0.0)
gconf-sharp (2.24.0.0)
Banshee.Gnome (2.6.0.0)
Banshee.NowPlaying (2.6.0.0)
System.Xml (4.0.0.0)
Banshee.Core (2.6.0.0)
Hyena.Data.Sqlite (2.6.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.6.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (2.6.0.0)
Mono.Posix (4.0.0.0)
gtk-sharp (2.12.0.0)
Banshee.ThickClient (2.6.0.0)
Nereid (2.6.0.0)
DBus.Proxies (0.0.0.0)
dbus-sharp-glib (1.0.0.0)
System.Core (4.0.0.0)
Hyena (2.6.0.0)
dbus-sharp (1.0.0.0)
glib-sharp (2.12.0.0)
System (4.0.0.0)
Banshee.Services (2.6.0.0)
Banshee (2.6.0.0)
mscorlib (4.0.0.0)


Platform Information: Linux 3.8.0-19-generic x86_64 x86_64 GNU/Linux


Disribution Information:


[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"


[/etc/os-release]
NAME="Ubuntu"
VERSION="13.04, Raring Ringtail"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 13.04"
VERSION_ID="13.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


[/etc/debian_version]
wheezy/sid


and banshee --debug 

[25 Debug 12:53:15.965] Starting
[25 Debug 12:53:16.048] Initialized MediaProfileManager: 0.078577
[25 Debug 12:53:16.073] GStreamer pipeline does not run: audioconvert ! novellaacenc bitrate=128000 profile=2 outputformat=0 ! novellqtmux
[25 Debug 12:53:16.074] GStreamer pipeline does not run: audioconvert ! faac bitrate=128000 outputformat=1 ! ffmux_mp4
[25 Debug 12:53:16.084] GStreamer pipeline does not run: audioconvert ! xingenc bitrate=128 ! id3v2mux


(Banshee:2938): GStreamer-WARNING **: 0.10-style raw audio caps are being created. Should be audio/x-raw,format=(string).. now.
[25 Debug 12:53:16.089] GStreamer pipeline does not run: audioresample ! audioconvert ! audio/x-raw-int, format=(string)S16LE, rate=(int)44100, channels=(int)2 ! wavenc
[25 Debug 12:53:16.093] GStreamer pipeline does not run: audioconvert ! fluwmaenc bitrate=64000 vbr=false ! fluasfmux
[25 Debug 12:53:16.102] Core service started (TranscoderService, 0.002509)
[25 Debug 12:53:16.103] Starting
[25 Debug 12:53:16.108] Transcoding file:///home/ryan/Music/Banshee/Music/Black%20Stone%20CherryBlack%20Stone%20Cherry/Folklore%20and%20Superstition/01%20-%20Blind%20Man.m4a to file:///home/ryan/.cache/banshee-1/transcoder/28877d64-015c-4d0b-9281-85d2e787bd8b.mp3


(Banshee:2938): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.36.0/./gobject/gsignal.c:2475: signal `new-decoded-pad' is invalid for instance `0x3c26a00' of type `GstDecodeBin'
[25 Debug 12:53:16.129] Finished - Adding 1 of 13 to PHILIPS
Object reference not set to an instance of an object
System.NullReferenceException: Object reference not set to an instance of an object
at Banshee.Sources.PrimarySource.IncrementAddedTracks () [0x00010] in /build/buildd/banshee-2.6.1/src/Core/Banshee.Services/Banshee.Sources/PrimarySource.cs:666
at Banshee.Dap.DapSource.OnTrackTranscodeError (Banshee.Collection.TrackInfo) [0x00020] in /build/buildd/banshee-2.6.1/src/Dap/Banshee.Dap/Banshee.Dap/DapSource.cs:440
at Banshee.MediaEngine.TranscoderService.OnError (object,Banshee.MediaEngine.TranscoderErrorArgs) [0x00031] in /build/buildd/banshee-2.6.1/src/Core/Banshee.Services/Banshee.MediaEngine/TranscoderService.cs:252
at Banshee.GStreamer.Transcoder.OnError (Banshee.Collection.TrackInfo,string) [0x0000d] in /build/buildd/banshee-2.6.1/src/Backends/Banshee.GStreamer/Banshee.GStreamer/Transcoder.cs:158
at Banshee.GStreamer.Transcoder.OnNativeError (intptr,intptr,intptr) [0x0005b] in /build/buildd/banshee-2.6.1/src/Backends/Banshee.GStreamer/Banshee.GStreamer/Transcoder.cs:135
at (wrapper native-to-managed) Banshee.GStreamer.Transcoder.OnNativeError (intptr,intptr,intptr) <IL 0x00024, 0x00083>
at (wrapper managed-to-native) Gtk.Application.gtk_main () <IL 0x00008, 0x00054>
at Gtk.Application.Run () <IL 0x00000, 0x0000b>
at Banshee.Gui.GtkBaseClient.Run () [0x00000] in /build/buildd/banshee-2.6.1/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:218
at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in /build/buildd/banshee-2.6.1/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:83
at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) [0x00044] in /build/buildd/banshee-2.6.1/src/Hyena/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:54





please help ryan

---

