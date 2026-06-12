---
title: "Banshee: cannot send null variant!!!"
date: 2008-11-01
forum: Multimedia Software
---

### Post by alessiofachechi on 2008-11-01
I've encountered a problem with banshee running. This problem appears only with some songs that have not all tag full (for example the album tag is empty) and when on a terminal i write this command:

> banshee --query-title

an error window appears: "Cannot send null variant" and the details are

> È stata lanciata un'eccezione non gestita: Cannot send null variant

at NDesk.DBus.MessageWriter.Write (object) <0x00059>
at NDesk.DBus.MessageWriter.Write (System.Type,object) <0x000c9>
at NDesk.DBus.MessageWriter.WriteFromDict (System.Type,System.Type,System.Collections.IDictionary) <0x00115>
at NDesk.DBus.MessageWriter.Write (System.Type,object) <0x001f3>
at NDesk.DBus.MessageHelper.ConstructDynamicReply (NDesk.DBus.MethodCall,System.Reflection.MethodInfo,object,object[]) <0x000f9>
at NDesk.DBus.ExportObject.HandleMethodCall (NDesk.DBus.MethodCall) <0x0035c>
at NDesk.DBus.Connection.HandleMethodCall (NDesk.DBus.MethodCall) <0x00372>
at NDesk.DBus.Connection.HandleMessage (NDesk.DBus.Message) <0x00123>
at NDesk.DBus.Connection.Iterate () <0x00023>
at <>c__CompilerGenerated0.<>c__AnonymousMethod1 (intptr,NDesk.GLib.IOCondition,intptr) <0x00027>
at (wrapper native-to-managed) <>c__CompilerGenerated0.<>c__AnonymousMethod1 (intptr,NDesk.GLib.IOCondition,intptr) <0x0004b>
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
at Gtk.Application.Run () <0x00007>
at Banshee.Gui.GtkBaseClient.Run () <0x00052>
at Banshee.Gui.GtkBaseClient.Startup () <0x00034>
at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x000a2>


.NET Version: 2.0.50727.42
OS Version: Unix 2.6.27.7

Assembly Version Information:

System.Configuration (2.0.0.0)
System.Web (2.0.0.0)
ipod-sharp (0.0.1.0)
Mtp (1.2.1.19132)
avahi-sharp (1.0.0.0)
Mono.Zeroconf.Providers.Avahi (2.0.0.76)
Mono.Zeroconf (2.0.0.76)
Banshee.Dap.Mtp (1.2.1.19141)
Banshee.Dap.MassStorage (1.2.1.19141)
taglib-sharp (2.0.3.0)
Mono.Media (1.2.1.19131)
Banshee.InternetRadio (1.2.1.19145)
Banshee.PlayQueue (1.2.1.19149)
Banshee.FileSystemQueue (1.2.1.19145)
Migo (1.2.1.19131)
Banshee.Podcasting (1.2.1.19149)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (1.2.1.19147)
Lastfm (1.2.1.19133)
Banshee.Lastfm (1.2.1.19146)
Banshee.AudioCd (1.2.1.19142)
Banshee.CoverArt (1.2.1.19143)
Banshee.Bookmarks (1.2.1.19142)
Banshee.Daap (1.2.1.19144)
Banshee.MultimediaKeys (1.2.1.19147)
pango-sharp (2.12.0.0)
Mono.Cairo (2.0.0.0)
Banshee.Widgets (1.2.1.19136)
Banshee.Dap.Ipod (1.2.1.19140)
Banshee.Dap (1.2.1.19140)
Banshee.Hal (1.2.1.19150)
Banshee.Unix (1.2.1.19151)
Banshee.GStreamer (1.2.1.19151)
gconf-sharp (2.20.0.0)
Banshee.Gnome (1.2.1.19150)
Banshee.NowPlaying (1.2.1.19148)
System.Transactions (2.0.0.0)
System.Xml (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
Mono.Addins (0.3.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.2.1.19130)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
gtk-sharp (2.12.0.0)
Hyena (1.2.1.19129)
System (2.0.0.0)
glib-sharp (2.12.0.0)
gdk-sharp (2.12.0.0)
Banshee.Core (1.2.1.19134)
Banshee.Services (1.2.1.19135)
Banshee.ThickClient (1.2.1.19138)
Nereid (1.2.1.19139)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.27-7-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

[/etc/debian_version]
lenny/sid

---

