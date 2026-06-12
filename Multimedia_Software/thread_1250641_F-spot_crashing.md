---
title: "F-spot crashing"
date: 2009-08-26
forum: Multimedia Software
---

### Post by t1m on 2009-08-26
Hi,

F-Spot keeps crashing on me. I have used it to download photos before; I've used the slideshow feature (which was slow on this computer). But all of a sudden it seems to be crashing at random times.

Here's the output of [FONT="Courier New"]f-spot[/FONT] in terminal:
```

$ f-spot
[Info  19:33:56.574] Initializing DBus
[Info  19:33:57.178] Initializing Mono.Addins
[Info  19:33:58.110] Starting new FSpot server
get fences failed: -1
param: 6, val: 0
[Info  19:34:03.269] Starting BeagleService
[Info  19:34:03.272] Hack for gnome-settings-daemon engaged
item ImportCommand+SourceItem
Testing gphoto path = usb:
PortInfo Universal Serial Bus, usb:

(f-spot:8207): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 50519 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


```


Do I now suddenly not have enough RAM or something? Any ideas or suggestions?

---

### Post by aroneous on 2009-11-04
Here's a bug describing the same problem:
[https://bugs.launchpad.net/ubuntu/+source/gnome-themes-ubuntu/+bug/411941](https://bugs.launchpad.net/ubuntu/+source/gnome-themes-ubuntu/+bug/411941)

It's an issue with the New Wave theme (well, for the bug submitter and me, anyway). Changing to another theme lets f-spot start.

---

### Post by kapkevin on 2009-11-04
> **aroneous said:**
> Here's a bug describing the same problem:
[https://bugs.launchpad.net/ubuntu/+source/gnome-themes-ubuntu/+bug/411941](https://bugs.launchpad.net/ubuntu/+source/gnome-themes-ubuntu/+bug/411941)

It's an issue with the New Wave theme (well, for the bug submitter and me, anyway). Changing to another theme lets f-spot start.

I'm not on the New Wave Theme and haven't had a chance to change the theme in f-spot, so f-spot is still on the default theme.

---

### Post by t1m on 2009-11-10
Yay! That fixed it for me--I just switched to using the "Dust" theme. Now F-Spot is working and I don't have to manually copy my photos using Nautilus.

Thank you. ;)

---

### Post by beyboo on 2009-11-22
Had the same problem me too - Changing from New wave to something else helped. Thanks !

---

### Post by jackcholt on 2009-11-25
[FONT="Arial"]I tried switching from the New Wave theme to Clear Looks and it didn't help.  I'm running Karmic. Here is the stack dump I get.  F-Spot dies immediately.
[/FONT]

An unhandled exception was thrown: Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at Mono.Addins.RuntimeAddin.CreateInstance (System.String typeName, Boolean throwIfNotFound) [0x00000] 
  at Mono.Addins.RuntimeAddin.CreateInstance (System.String typeName) [0x00000] 
  at FSpot.Widgets.SidebarPageNode.GetSidebarPage () [0x00000] 
  at MainWindow.OnSidebarExtensionChanged (System.Object s, Mono.Addins.ExtensionNodeEventArgs args) [0x00000] 
  at Mono.Addins.ExtensionNode.OnChildNodeAdded (Mono.Addins.ExtensionNode node) [0x00000] 
  at Mono.Addins.ExtensionNode.NotifyChildChanged () [0x00000] 
  at Mono.Addins.TreeNode.NotifyChildrenChanged () [0x00000] 
  at Mono.Addins.ExtensionContext.NotifyConditionChanged (Mono.Addins.ConditionType cond) [0x00000] 
  at Mono.Addins.ExtensionContext.OnConditionChanged (System.Object s, System.EventArgs a) [0x00000] 
  at Mono.Addins.ConditionType.NotifyChanged () [0x00000] 
  at FSpot.Extensions.ViewModeCondition.<ViewModeCondition>m__5 () [0x00000] 
  at FSpot.Extensions.ViewModeCondition.set_Mode (ViewMode value) [0x00000] 
  at FSpot.Widgets.Sidebar.HandleContextChanged (System.Object sender, System.EventArgs args) [0x00000] 
  at FSpot.Widgets.Sidebar.set_Context (ViewContext value) [0x00000] 
  at MainWindow..ctor (.Db db) [0x00000] 
  at FSpot.Core.get_MainWindow () [0x00000] 
  at FSpot.Core.Organize () [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 2.0.50727.1433

Assembly Version Information:

glade-sharp (2.12.0.0)
System.Core (3.5.0.0)
FSpot.Bling (0.0.0.0)
pango-sharp (2.12.0.0)
gtk-sharp-beans (2.14.0.0)
gnome-sharp (2.24.0.0)
System.Transactions (2.0.0.0)
System.Configuration (2.0.0.0)
FSpot.Widgets (0.0.0.0)
System.Xml (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
gconf-sharp (2.24.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
FSpot.Query (0.0.0.0)
FSpot.JobScheduler (0.0.0.0)
gdk-sharp (2.12.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
gnome-vfs-sharp (2.24.0.0)
Cms (0.0.0.0)
FSpot.Core (0.0.0.0)
FSpot.Platform (0.0.0.0)
Mono.Posix (2.0.0.0)
FSpot.Utils (0.0.0.0)
atk-sharp (2.12.0.0)
gtk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
System (2.0.0.0)
Mono.Addins.Setup (0.4.0.0)
glib-sharp (2.12.0.0)
f-spot (0.6.1.5)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.31-15-generic i686 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
squeeze/sid

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

---

### Post by tariqsheikh on 2010-02-17
I have the same problem after i selected the new wave theme. The problem is that I can not select another theme because f-spot crashes as soon as I run it. Any workaround for that?
My gtk2-engines-pixbuf is up to date.
f-spot --debug shows the following:

tariq@Sakura:~$ f-spot --debug
** Running f-spot in Debug Mode **
** Running Mono with --debug   **

(/usr/lib/f-spot/f-spot.exe:12129): GLib-WARNING **: g_set_prgname() called multiple times
[Info  00:43:37.508] Initializing DBus
[Debug 00:43:38.423] DBusInitialization took 0.851809s
[Info  00:43:38.423] Initializing Mono.Addins
[Debug 00:43:39.666] Mono.Addins Initialization took 1.243268s
[Info  00:43:39.738] Starting new FSpot server (f-spot 0.6.1.5)
[Debug 00:43:40.946] Db Initialization took 0.599384s

** (/usr/lib/f-spot/f-spot.exe:12129): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:12129): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:12129): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:12129): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:12129): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Debug 00:43:42.336] Query Started : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 00:43:42.366] QueryToTemp took 0.03048s : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 00:43:42.366] Reloading the query took 0.035969s
[Debug 00:43:42.772] PhotosPerMonth took 0.014625s
[Debug 00:43:42.775] TimeAdaptor REAL Reload took 0.266692s
[Debug 00:43:44.080] Query Started : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 00:43:44.252] QueryToTemp took 0.172271s : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 00:43:44.501] PhotosPerMonth took 0.040767s
[Debug 00:43:44.502] TimeAdaptor REAL Reload took 0.246166s
[Debug 00:43:44.761] Reloading the query took 0.682558s
[Debug 00:43:44.769] Query Started : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 00:43:44.806] QueryToTemp took 0.036233s : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 00:43:44.885] Reloading the query took 0.115464s
[Info  00:43:44.897] Starting BeagleService
[Debug 00:43:44.899] BeagleService startup took 3.6E-05s
[Debug 00:43:45.016] PhotosPerMonth took 0.004131s
[Debug 00:43:45.017] TimeAdaptor REAL Reload took 0.210618s
[Info  00:43:45.033] Hack for gnome-settings-daemon engaged

(/usr/lib/f-spot/f-spot.exe:12129): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
Stacktrace:

  ...

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

---

### Post by t1m on 2010-02-17
Quick suggestion/question: did you change the theme in F-Spot's preferences (Edit->Preferences), or the general Gnome theme? (System->Preferences->Appearance; that is, *if* you're using Gnome and not KDE or XFCE)

---

### Post by tariqsheikh on 2010-02-18
> **t1m said:**
> Quick suggestion/question: did you change the theme in F-Spot's preferences (Edit->Preferences), or the general Gnome theme? (System->Preferences->Appearance; that is, *if* you're using Gnome and not KDE or XFCE)

I changed the theme in F-Spot's preferences (Edit->Preferences), and my Gnome theme is the default one. I have not touched the Gnome theme.

---

### Post by t1m on 2010-02-21
Hmm. I would have thought you could change F-Spot's theme back by using the gconf Configuration Editor (press Alt+F2, type gconf-editor, enter)--but I couldn't figure out where in gconf-editor to do it...Any one know? Otherwise, perhaps try "completely removing" f-spot in Synaptic Package Manager?

(I meant to get back sooner, sorry; hadn't had time...)

---

### Post by jnah on 2010-02-28
Run gconf-editor, select apps then f-spot then ui.

Then delete the tag which has the theme in it (gtkrc I think, and it probably contains the text new wave).

f-spot should then start up OK.

This bug has been reported here [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/520186?comments=all](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/520186?comments=all)

---

### Post by tariqsheikh on 2010-03-13
> **jnah said:**
> Run gconf-editor, select apps then f-spot then ui.

Then delete the tag which has the theme in it (gtkrc I think, and it probably contains the text new wave).

f-spot should then start up OK.

This bug has been reported here [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/520186?comments=all](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/520186?comments=all)

Thanks a lot jnah, that solved my problem. :D

---

