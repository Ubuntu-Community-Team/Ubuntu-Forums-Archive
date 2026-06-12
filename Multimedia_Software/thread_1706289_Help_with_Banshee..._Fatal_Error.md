---
title: "Help with Banshee... Fatal Error"
date: 2011-03-13
forum: Multimedia Software
---

### Post by falsedichotomies on 2011-03-13
Using 10.10, playing around with Ubuntu for the first time, and I think I went messing around with stuff that I shouldn't have. After purging banshee from my system, I noticed that there were still many files attached to it when I did a search for its name in nautilus, so I deleted them as well. Then, I had a change of heart and decided to give the program another chance. The only problem is that after a reinstall, when I try to load Banshee I get the following fatal error:

```
:~$ banshee-1
[Info  20:58:51.569] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-11-26 13:53:04 UTC]
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

```

That seems like a lot of "at"s to me. Would it be easier to just clean install Ubuntu than try to fix each one or is there a simple way to do this?

---

### Post by shredder12 on 2011-03-13
Just in case, try installing mono-addins
```
[shell]$ sudo apt-get install libmono-addins-gui0.2-cil
```
And if that doesn't work try running banshee with the "--debug" option. This'll give us a better idea of the problem.
```
[shell]$ banshee-1 --debug
```

---

### Post by falsedichotomies on 2011-03-13
Certainly. Thanks for the quick reply and the help. It would appear as if I already the latest version of libmono-addins.

```
:~$ sudo apt-get install libmono-addins-gui0.2-cil
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmono-addins-gui0.2-cil is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
]
```

As for trying to run in debug mode. That doesn't seem to work either. It gives me the same errors as before (I think).

```
:~$ banshee-1 --debug
** Running Mono with --debug   **
[1 Info  21:52:56.940] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-11-26 13:53:04 UTC]
[1 Debug 21:52:56.959] Initializing GTK
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

(Banshee:17254): IBUS-WARNING **: Connect to unix:abstract=/tmp/dbus-dxGeriuSiT,guid=3d039d2f27b201f460c745e9000014aa failed: Failed to connect to socket /tmp/dbus-dxGeriuSiT: Connection refused.

```

I think I learned my lesson here. I am not going to mess with stuff as root if I don't know what it is.

---

### Post by shredder12 on 2011-03-13
I believe you accidently removed some of the crucial libraries. One thing that we can do is by trying to reinstall the core packages required by banshee. When I installed banshee on a VM, it required the following packages
```
banshee-extension-soundmenu banshee-extensions-common libgdata1.4-cil
  libgkeyfile1.0-cil libgudev1.0-cil libindicate0.1-cil
  libmono-zeroconf1.0-cil

```
I am not sure if this will fix the issue but you may try reinstalling these packages. If some files were deleted, they'll be re-established.
And, btw I guess you can try the debug thing again after installing the package "banshee-dbg"
```
sudo apt-get install banshee-dbg
```

---

### Post by falsedichotomies on 2011-03-13
Nope. No luck. All the packages you listed I already have installed (I believe they come with banshee from the repository) and banshee-dbg doesn't help either.

Very interesting.

---

### Post by shredder12 on 2011-03-13
I am clueless too. Btw, I was going for re-installation of packages because if you have deleted some of the files of those packages by mistake, then may be re-installing them would restore those files(libraries etc.)
Other than this I really don't know what the trouble could be.

---

### Post by falsedichotomies on 2011-03-13
Awesome! I figured it out!

Apparently, it was some kind of mono.addins bug that required me to delete the banshee configuration files at ~/.config/banshee/

Anyone interested can read more about it here:

[http://banshee-media-player.2283330.n4.nabble.com/quot-Could-not-read-add-in-description-quot-error-on-startup-td2983558.html](http://banshee-media-player.2283330.n4.nabble.com/quot-Could-not-read-add-in-description-quot-error-on-startup-td2983558.html)

Thanks for all your help shredder12! :D

Now I don't feel like such a fool anymore.

---

### Post by shredder12 on 2011-03-13
wow! that was some solution. 
and you're always welcome :D

---

