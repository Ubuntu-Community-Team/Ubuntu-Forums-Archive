---
title: "Banshee Media Player crashes when opening"
date: 2010-03-28
forum: Multimedia Software
---

### Post by chrissy.millichamp on 2010-03-28
Each time when I start Banshee Media Player it crashes or I get the error message fatal error, I want to know what occurred to Banshee Media of being in a such state and what could I do to fix this problem.

---

### Post by Enigmapond on 2010-03-28
If you are using any other version but 1.5.6, then add the PPA [https://launchpad.net/~banshee-team/+archive/ppa]("https://launchpad.net/%7Ebanshee-team/+archive/ppa") and update to this version. There was a problem but now it's fixed.

Cheers!

EDIT: ```
sudo add-apt-repository ppa:banshee-team/ppa
```

```
sudo apt-get update && sudo apt-get upgrade
``` [FONT=Verdana]****[/FONT]

---

### Post by n0dix on 2010-03-28
What exactly is the error you got?

---

### Post by chrissy.millichamp on 2010-03-28
**It says precisely the following**:

[U]Banshee Media Player Encountered a Fatal Error
Exception has been thrown by the target of an invocation.[/U]
**and now the other following** _error details_:

An unhandled exception was thrown: SIGILL

  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] 

.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.32.17

Assembly Version Information:

Banshee.CoverWallpaper (0.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
Mirage (0.6.0.0)
Banshee.Mirage (0.6.0.0)
Banshee.AudioCd (1.5.0.0)
Banshee.CoverArt (1.5.0.0)
Banshee.Bookmarks (1.5.0.0)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (1.5.0.0)
Lastfm (1.5.0.0)
Banshee.Daap (1.5.0.0)
taglib-sharp (2.0.3.7)
Migo (1.5.0.0)
Banshee.Podcasting (1.5.0.0)
Banshee.MultimediaKeys (1.5.0.0)
Banshee.Bpm (1.5.0.0)
Banshee.Wikipedia (1.5.0.0)
webkit-sharp (1.1.15.0)
Banshee.Lyrics (0.0.0.0)
Banshee.Lastfm (1.5.0.0)
pango-sharp (2.12.0.0)
Banshee.Widgets (1.5.0.0)
Banshee.Dap.Ipod (1.5.0.0)
Banshee.Dap (1.5.0.0)
Banshee.Hal (1.5.0.0)
Banshee.Unix (1.5.0.0)
Banshee.GStreamer (1.5.0.0)
Mono.Media (1.5.0.0)
System.Transactions (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
gconf-sharp (2.24.0.0)
Banshee.Gnome (1.5.0.0)
Banshee.NowPlaying (1.5.0.0)
Mono.Cairo (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.Sqlite (1.5.0.0)
System.Xml (2.0.0.0)
System.Core (3.5.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.5.0.0)
gtk-sharp (2.12.0.0)
Banshee.Core (1.5.0.0)
Banshee.ThickClient (1.5.0.0)
Nereid (1.5.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
System (2.0.0.0)
Hyena (1.5.0.0)
NDesk.DBus (1.0.0.0)
glib-sharp (2.12.0.0)
Banshee.Services (1.5.0.0)
Banshee (1.5.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.32-17-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu lucid (development branch)"

[/etc/debian_version]
squeeze/sid

---

### Post by n0dix on 2010-03-28
Try with the suggestion if @Enigmapond. The output didn't say so much :(

---

### Post by chrissy.millichamp on 2010-03-29
what do mean by output?

---

### Post by n0dix on 2010-03-29
The error you post in the 4th message.

---

### Post by chrissy.millichamp on 2010-03-29
Well I actually did apply the suggestion that he gave me, and it didnt do anything. I did as i possibly could about giving the necessary info. I cant possibly do more than already did.

---

### Post by gazambuja on 2010-04-15
to me, the problem is BPM detection, Deactivating the option:

Edit > Preferences > Source Specific > Automatically detect BMP for all songs

---

### Post by anubiscaller on 2010-04-19
I'm having the same issue - Banshee immediately crashes upon opening, without an error message. So obviously, we can't use the suggestion above.

Any ideas?

---

