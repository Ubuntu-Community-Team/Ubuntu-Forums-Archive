---
title: "Problem while importing Photos to F-Spot"
date: 2010-07-04
forum: Multimedia Software
---

### Post by Mandarine on 2010-07-04
Hi,

I've been running F-Spot on my UNR 10.04 installation for a couple of weeks now. Everything worked fine.

Today I tried to import some pictures from my Canon Digital Camera and F-Spot crashes ...

"File name must be absolute"
```
Eine unverarbeitete Ausnahme trat auf:Filename path must be absolute

  at Hyena.SafeUri.FilenameToUri (System.String localPath) [0x00000] 
  at Hyena.SafeUri..ctor (System.String uri) [0x00000] 
  at FSpot.App.HandleImport (System.String path) [0x00000] 
  at FSpot.App.Import (System.String path) [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 2.0.50727.1433

Assembly Version Information:

FSpot.Exporters.RetroactiveRoll (0.7.0.0)
FSpot.Exporters.CDExport (0.7.0.0)
FSpot.Exporters.FlickrExport (0.7.0.0)
FSpot.Exporters.ScreensaverConfig (0.7.0.0)
FSpot.Exporters.GalleryExport (0.7.0.0)
FSpot.Exporters.PicasaWeb (0.7.0.0)
FSpot.Exporters.HashJob (0.7.0.0)
FSpot.Exporters.FolderExport (0.7.0.0)
FSpot.Exporters.SmugMugExport (0.7.0.0)
SemWeb (0.7.1.0)
gio-sharp (2.14.0.0)
glade-sharp (2.12.0.0)
FSpot.Bling (0.7.0.0)
pango-sharp (2.12.0.0)
FSpot.Query (0.7.0.0)
gnome-sharp (2.24.0.0)
System.Transactions (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
gtk-sharp-beans (2.14.0.0)
FSpot.JobScheduler (0.7.0.0)
System.Configuration (2.0.0.0)
FSpot.Widgets (0.7.0.0)
System.Xml (2.0.0.0)
gconf-sharp (2.24.0.0)
System.Core (3.5.0.0)
unique-sharp (1.0.0.0)
System (2.0.0.0)
Mono.Addins (0.4.0.0)
FSpot.Cms (0.7.0.0)
FSpot.Core (0.7.0.0)
FSpot.Platform (0.7.0.0)
Mono.Posix (2.0.0.0)
gdk-sharp (2.12.0.0)
Hyena (0.7.0.0)
atk-sharp (2.12.0.0)
gtk-sharp (2.12.0.0)
Mono.Addins.Setup (0.4.0.0)
glib-sharp (2.12.0.0)
FSpot.Utils (0.7.0.0)
f-spot (0.7.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.32-23-generic i686 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
squeeze/sid

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"

```

Just running F-Spot works fine. It only crashes when trying to import pictures from my camera.

Importing the Pictures directly from the SC-Card or any other folder works.

I already tried formating the SC-Card in the camera and the tips from this post:[http://ubuntuforums.org/showthread.php?t=1250641]("http://ubuntuforums.org/showthread.php?t=1250641") 

Both tricks didn't do the job.

Any other suggestions?

Sascha

---

### Post by Mandarine on 2010-07-09
can't anybody help?

---

### Post by PasQty on 2010-07-20
[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/603885](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/603885)

---

### Post by orion940 on 2010-08-13
It has not gotten fixed in 0.7.2.  Im trying to import from Canon Power Shot.

An unhandled exception was thrown: Filename path must be absolute

  at Hyena.SafeUri.FilenameToUri (System.String localPath) [0x00000] 
  at Hyena.SafeUri..ctor (System.String uri) [0x00000] 
  at FSpot.App.HandleImport (System.String path) [0x00000] 
  at FSpot.App.Import (System.String path) [0x00000] 
  at FSpot.Driver.Startup () [0x00000] 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] 

.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.32.24

Assembly Version Information:

FSpot.Tools.RetroactiveRoll (0.7.0.0)
FSpot.Tools.HashJob (0.7.0.0)
FSpot.Tools.ScreensaverConfig (0.7.0.0)
FSpot.Exporters.Gallery (0.7.0.0)
FSpot.Exporters.Flickr (0.7.0.0)
FSpot.Exporters.CD (0.7.0.0)
FSpot.Exporters.SmugMug (0.7.0.0)
FSpot.Exporters.Folder (0.7.0.0)
FSpot.Exporters.PicasaWeb (0.7.0.0)
glade-sharp (2.12.0.0)
FSpot.Bling (0.7.0.0)
TagLib (0.7.0.0)
pango-sharp (2.12.0.0)
FSpot.Query (0.7.0.0)
gnome-sharp (2.24.0.0)
System.Transactions (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.Sqlite (0.7.0.0)
gtk-sharp-beans (2.14.0.0)
Hyena.Data.Sqlite (0.7.0.0)
FSpot.JobScheduler (0.7.0.0)
System.Core (3.5.0.0)
unique-sharp (1.0.0.0)
System.Configuration (2.0.0.0)
FSpot.Gui (0.7.0.0)
System.Xml (2.0.0.0)
Mono.Addins (0.4.0.0)
gio-sharp (2.14.0.0)
gconf-sharp (2.24.0.0)
Hyena.Gui (0.7.0.0)
atk-sharp (2.12.0.0)
System (2.0.0.0)
Mono.Addins.Setup (0.4.0.0)
gtk-sharp (2.12.0.0)
FSpot.Cms (0.7.0.0)
FSpot.Core (0.7.0.0)
FSpot.Platform (0.7.0.0)
Mono.Posix (2.0.0.0)
gdk-sharp (2.12.0.0)
Hyena (0.7.0.0)
glib-sharp (2.12.0.0)
FSpot.Utils (0.7.0.0)
f-spot (0.7.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.32-24-generic-pae i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

[/etc/debian_version]
squeeze/sid

---

