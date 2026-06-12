---
title: "Banshee encountered a fatal error"
date: 2008-05-24
forum: Multimedia Software
---

### Post by lamps06 on 2008-05-24
Howdy.  I just installed the latest update for Banshee through Synaptic Update Manager and now it will not launch.  I get the message that ¨Banshee encountered a fatal error¨ and then this string of error messages:

An unhandled exception was thrown: duplicate column name: ExternalID

  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.SqliteClient.SqliteConnection connection) [0x00093] in /build/buildd/banshee-1-0.99.2/src/Libraries/Hyena/Hyena.Data.Sqlite/HyenaSqliteCommand.cs:116 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] 
  at Banshee.Database.BansheeDbFormatMigrator.InnerMigrate () [0x000ae] in /build/buildd/banshee-1-0.99.2/src/Core/Banshee.Services/Banshee.Database/BansheeDbFormatMigrator.cs:176 
  at Banshee.Database.BansheeDbFormatMigrator.Migrate () [0x00018] in /build/buildd/banshee-1-0.99.2/src/Core/Banshee.Services/Banshee.Database/BansheeDbFormatMigrator.cs:136 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in /build/buildd/banshee-1-0.99.2/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:55 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00048] in /build/buildd/banshee-1-0.99.2/src/Libraries/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:54 

.NET Version: 2.0.50727.42
OS Version: Unix 2.6.24.16

Assembly Version Information:

System.Transactions (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
System.Xml (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
Mono.Addins (0.3.0.0)
gdk-sharp (2.12.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (0.99.2.13426)
Mono.Posix (2.0.0.0)
gtk-sharp (2.12.0.0)
glib-sharp (2.12.0.0)
Banshee.Core (0.99.2.13429)
Hyena (0.99.2.13425)
System (2.0.0.0)
Banshee.Services (0.99.2.13431)
Banshee.ThickClient (0.99.2.13433)
Nereid (0.99.2.13434)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.24-16-rt i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

[/etc/debian_version]
lenny/sid




Does anyone know what this means or what I can do to correct this problem?  Thank you.

---

### Post by lamps06 on 2008-05-28
Has anyone else encountered this or a similar error?  It is pretty debilitating as I can no longer run my main MP3 player.  Audacious now seems to have stopped working as well.  Not sure if this is a related issue or not.  I could really use some help.  Anyone?

---

### Post by chri2020 on 2008-05-29
hey,
check out this thread here:
[http://ubuntuforums.org/showthread.php?p=5024382](http://ubuntuforums.org/showthread.php?p=5024382)

isaacj87 found a solution,
you have to move the dir ~/.config/banshee-1, or delete it.
then banshee should run again,

---

### Post by lamps06 on 2008-05-31
Thank you, Chri2020, that seemed to do the trick!  However, this opens up another question.  When I first deleted that directory and relaunched Banshee it had to rebuild the database for my music library.  Fine, that makes sense.  But after restarting my computer and relaunching Banshee it is again rebuilding this database.  Will this happen now every time I want to use Banshee?  Did I do something wrong or is there a way to avoid this?

Also, two things that have always bugged me about Banshee:

1.  How do I get it to display album art in the bottom left corner?  In screen shots I always see this feature yet I cannot seem to enable it in my own Banshee.  I have checked the ¨Show cover art¨ box but that does not display it.  Is it some sort of plug-in I need to install?

2.  Also, I find it really annoying that you cannot add your own cover art, that Banshee insists on trying to find the cover art from an online databse.  Is there any way to turn this off and allow me to use my own cover art?  I have many albums that will never be in any online database but I do have cover art for them.

Thanks for your time!

---

### Post by mitchellcipriano on 2008-08-02
I had a very similar problem. I clicked on the about box after upgrading to Banshee 1.2. This caused my system to crash. After a reboot, when I tried to run Banshee I had a SQL error. I tried uninstalling and reinstalling, but this did not fix it. I then found the db file and deleted it and it was fixed. I am a little disappointed that Banshee was able to crash my system due to a DB error, but all is well now.

---

