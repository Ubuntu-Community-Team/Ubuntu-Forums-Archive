---
title: "need help! Moovila-pro cannot launch"
date: 2012-06-15
forum: Multimedia Software
---

### Post by kingpeng0318 on 2012-06-15
I purchased moovila-pro media center. i installed the 64 bit for ubuntu. but it crashes when start 
here is the error i got 


An unhandled exception was thrown: Could not load type 'Banshee.Database.BansheeDbConnection' from assembly 'Banshee.Services, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'.

  at Banshee.ServiceStack.ServiceManager.OnServiceStarted (IService service) [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.RegisterService (System.Type type) [0x00000] in <filename unknown>:0 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

.NET Version: 4.0.30319.1
OS Version: Unix 3.2.0.25

Assembly Version Information:

Mono.Data.Sqlite (0.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
System.Configuration (4.0.0.0)
Banshee.Gnome (0.0.0.0)
Banshee.NowPlaying (0.0.0.0)
Banshee.MovieControls (0.0.0.0)
System.Xml (4.0.0.0)
Mono.Posix (4.0.0.0)
Banshee.Core (0.0.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.6.0.0)
Hyena.Gui (0.0.0.0)
System (4.0.0.0)
System.Core (4.0.0.0)
Hyena (0.0.0.0)
atk-sharp (2.12.0.0)
glib-sharp (2.12.0.0)
gtk-sharp (2.12.0.0)
Banshee.Services (0.0.0.0)
Banshee.ThickClient (0.0.0.0)
Moovida-Pro (2.1.1.0)
mscorlib (4.0.0.0)

Platform Information: Linux 3.2.0-25-generic x86_64 x86_64 GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

[/etc/debian_version]
wheezy/sid


Can someone help me?

---

### Post by directhex on 2012-06-15
Try contacting Fluendo support directly - their forked version of Banshee behaves differently to the regular one in many ways, so I'm not sure how to decipher their stack traces.

---

