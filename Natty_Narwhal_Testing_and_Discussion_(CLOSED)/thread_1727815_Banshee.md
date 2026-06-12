---
title: "Banshee"
date: 2011-04-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mdhollis on 2011-04-13
Anyone else having this issue?  When i try to start banshee it crashes.  I get this error:

Exception has been thrown by the target of an invocation.
```
An unhandled exception was thrown: Could not read add-in description

  at Mono.Addins.Addin.get_Description () [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.CheckHostAssembly (System.Reflection.Assembly asm) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.ActivateRoots () [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.Initialize () [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinManager.Initialize (System.String configDir) [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.InitializeAddins () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.DefaultInitialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.Application.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] in <filename unknown>:0 
  at Nereid.Client..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.38.8

Assembly Version Information:

System.Xml (2.0.0.0)
Banshee.Core (2.0.0.0)
Hyena.Data.Sqlite (2.0.0.0)
System.Core (3.5.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (2.0.0.0)
gtk-sharp (2.12.0.0)
Banshee.ThickClient (2.0.0.0)
Nereid (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
Hyena (2.0.0.0)
NDesk.DBus (1.0.0.0)
glib-sharp (2.12.0.0)
System (2.0.0.0)
Banshee.Services (2.0.0.0)
Banshee (2.0.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.38-8-generic-pae i686 i386 GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu Natty (development branch)"

[/etc/debian_version]
squeeze/sid

```

This is the log:

```
exec -a banshee mono  /usr/lib/banshee/Banshee.exe    --redirect-log --play-enqueued

[Info  01:07:08.818] Running Banshee 2.0.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2011-04-08 22:47:09 UTC]
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.InvalidOperationException: Could not read add-in description
  at Mono.Addins.Addin.get_Description () [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.CheckHostAssembly (System.Reflection.Assembly asm) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.ActivateRoots () [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.Initialize () [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinManager.Initialize (System.String configDir) [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.InitializeAddins () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.DefaultInitialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.Application.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] in <filename unknown>:0 
  at Nereid.Client..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 
Full thread dump:

"<unnamed thread>" tid=0x0xb759a6f0 this=0x0x3eed8 thread handle 0x404 state : not waiting owns ()
  at (wrapper managed-to-native) Gtk.Dialog.gtk_dialog_run (intptr) <0x00004>
  at (wrapper managed-to-native) Gtk.Dialog.gtk_dialog_run (intptr) <0x00004>
  at Gtk.Dialog.Run () <0x00016>
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x00106>
  at Banshee.Gui.GtkBaseClient.Startup<object> () <0x0005c>
  at Banshee.Gui.GtkBaseClient.Startup<object> (string[]) <0x000d8>
  at Nereid.Client.Main (string[]) <0x00015>
  at (wrapper runtime-invoke) <Module>.runtime_invoke_void_object (object,intptr,intptr,intptr) <0x00043>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) <0x0002e>
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00025>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00067>
  at System.AppDomain.ExecuteAssembly (string) <0x00019>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <0x00057>
  at Booter.Booter.BootClient (string) <0x00069>
  at Booter.Booter.Main () <0x001a0>
  at (wrapper runtime-invoke) object.runtime_invoke_void (object,intptr,intptr,intptr) <0x0003a>
```

Happens to me in maverick too, but I was able to downgrade banshee to get it to work.  I filed a bug about it.  Just wondering if I was the only one because I was having other issues with banshee(mainly related to ipod syncing).

[https://bugzilla.gnome.org/show_bug.cgi?id=647412]("https://bugzilla.gnome.org/show_bug.cgi?id=647412")

---

### Post by bluenova on 2011-04-13
There are at least 2 of us since the latest updates.

---

### Post by zika on 2011-04-13
Is there any simle way to import radio stations from Rhythmbox to Banshee...?
Is there any simle way to import radio stations from Rhythmbox to DeadBeef...?

---

### Post by VinDSL on 2011-04-13
> **mdhollis said:**
> Anyone else having this issue?  When i try to start banshee it crashes.
I'm using Banshee right now.

It's behaving very well, actually...  ;)

---

### Post by nothingspecial on 2011-04-13
It refuses to handle my music library without crashing 35,000+ songs.

---

### Post by KegHead on 2011-04-13
Hi!

No problems here!

11.04b2/classic/2.6.39-999.

KewgHead

---

### Post by iForce1 on 2011-04-13
I have the same problem.

---

### Post by gnomeuser on 2011-04-13
> **zika said:**
> Is there any simle way to import radio stations from Rhythmbox to Banshee...?


If the default Rhythmbox importer in Banshee doesn't do this I think you should file a bug requesting it. It sounds like a sane and desirable feature.

see:
[http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/](http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/)

> 
Is there any simle way to import radio stations from Rhythmbox to DeadBeef...?

I doubt that is present.

As of the bug originally mentioned, it might be that the banshee-1 to banshee renaming got the extension database confused. Try running banshee --debug-addins once which should rebuild it. If not please do file the issue following the instructions given above.

---

### Post by nothingspecial on 2011-04-13
> **gnomeuser said:**
> 


As of the bug originally mentioned, it might be that the banshee-1 to banshee renaming got the extension database confused. Try running banshee --debug-addins once which should rebuild it. If not please do file the issue following the instructions given above.


Thanks, that seems to have fixed it, although I could be here all day waiting for it to scan my music :p

---

### Post by zika on 2011-04-13
> **gnomeuser said:**
> Try running banshee --debug-addins once which should rebuild it.It seems that this did the trick. I'll check again. Thank You!

---

### Post by bluenova on 2011-04-13
> **gnomeuser said:**
> Try running banshee --debug-addins once which should rebuild it.

Yep, thank you.

---

### Post by iForce1 on 2011-04-13
Is there any way to fix this error?

---

### Post by iForce1 on 2011-04-13
I got it to work. :)

Removed Banshee
deleted banshee-1 folder from /.config 
Install Banshee

:D

---

### Post by zika on 2011-04-13
> **zika said:**
> It seems that this did the trick. I'll check again. Thank You!Then I made a mistake and went the way that I sould not have taken: Purged Banshee, removed all banshee-1 folders and reinstalled Banshee. It imported all the stuff from Rhythmbox successfully, except Radio stations... 
Silly old man I am...

---

### Post by mdhollis on 2011-04-14
If I run banshee --debug-addins I get the same error message.  If I run sudo  banshee --debug-addins, it runs but only in the terminal.   If I try to launch it from my desktop I still get that error.  Am I doing something wrong?

---

### Post by mdhollis on 2011-04-14
> **gnomeuser said:**
> As of the bug originally mentioned, it might be that the banshee-1 to banshee renaming got the extension database confused. Try running banshee --debug-addins once which should rebuild it. If not please do file the issue following the instructions given above.

I did file a bug:

[https://bugzilla.gnome.org/show_bug.cgi?id=647412]("https://bugzilla.gnome.org/show_bug.cgi?id=647412")

---

### Post by gnomeuser on 2011-04-14
> **mdhollis said:**
> If I run banshee --debug-addins I get the same error message.  If I run sudo  banshee --debug-addins, it runs but only in the terminal.   If I try to launch it from my desktop I still get that error.  Am I doing something wrong?

You should never run Banshee with sudo.

Regardless this bug is now tracked here:

[https://bugzilla.gnome.org/show_bug.cgi?id=647412](https://bugzilla.gnome.org/show_bug.cgi?id=647412)

---

### Post by directhex on 2011-04-14
> **mdhollis said:**
> If I run sudo  banshee --debug-addins, it runs but only in the terminal.

You will no longer be able to run Banshee as a regular user, as some files are owned by root (and your regular user can't write to them).

To repair this damage, run "whoami" to see what your username is, then "sudo chown -R foo.foo ~/.config/banshee* ~/.cache/banshee*" where you replace "foo" with your username. This will give your user ownership of the files owned by root

---

### Post by mdhollis on 2011-04-14
> **directhex said:**
> You will no longer be able to run Banshee as a regular user, as some files are owned by root (and your regular user can't write to them).

To repair this damage, run "whoami" to see what your username is, then "sudo chown -R foo.foo ~/.config/banshee* ~/.cache/banshee*" where you replace "foo" with your username. This will give your user ownership of the files owned by root

Yeah I screwed up.  I've been at this all day.  Thanks for the help.  I share a home partition with 10.10 and 11.04.  I just realized that with banshee up to date in maverick it works fine.  When I update it in natty thats when I get this error and both 10.10 and 11.04.  Any ideas why that is?

---

### Post by zika on 2011-04-15
> **mdhollis said:**
> I share a home partition with 10.10 and 11.04.Is this wise?

---

### Post by nerdy_kid on 2011-04-15
> **zika said:**
> Is this wise?

shouldn't cause too many problems, I do the same thing.  I haven't booted into Maverick for a while, but last time I did everything was fine.  It was Kubuntu Maverick however, so most of the Natty config (which is all for GNOME) was most likely ignored.

---

### Post by mdhollis on 2011-04-15
> **zika said:**
> Is this wise?

I have no clue, lol.  But I try.

---

