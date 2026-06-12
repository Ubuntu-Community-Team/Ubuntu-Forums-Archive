---
title: "Banshee won't start: DLLNotFoundException"
date: 2010-06-21
forum: Multimedia Software
---

### Post by anfreita09 on 2010-06-21
Hello, I'm having some trouble with Banshee. Kind of stupid on my part, but I tried to install some plugins for banshee following instructions on this website: [http://ubuntuforums.org/showthread.php?t=202464](http://ubuntuforums.org/showthread.php?t=202464)

I got about halfway through and finally noticed it was for Banshee 0.10.0, so these instructions did not exactly work for 1.6.0. So now when I try to start banshee I get the following output:

```
[Info  16:59:34.437] Running Banshee 1.6.0: [Ubuntu lucid (development branch) (linux-gnu, x86_64) @ 2010-04-04 14:20:11 UTC]
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.TypeInitializationException: An exception was thrown by the type initializer for Banshee.Metrics.BansheeMetrics ---> System.DllNotFoundException: msvcrt
  at (wrapper managed-to-native) Mono.Unix.Native.Stdlib:free (intptr)
  at Mono.Unix.UnixMarshal.FreeHeap (IntPtr ptr) [0x00000] 
  at Mono.Unix.Catalog.GetString (System.String s) [0x00000] 
  at Banshee.Metrics.BansheeMetrics..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00000] 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] 
  at Nereid.Client..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] 

Unhandled Exception: System.DllNotFoundException: intl
  at (wrapper managed-to-native) Mono.Unix.Catalog:gettext (intptr)
  at Mono.Unix.Catalog.GetString (System.String s) [0x00000] 
  at Hyena.Gui.Dialogs.ExceptionDialog.BuildExceptionMessage (System.Exception e) [0x00000] 
  at Hyena.Gui.Dialogs.ExceptionDialog..ctor (System.Exception e) [0x00000] 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup[Client] () [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup[Client] (System.String[] args) [0x00000] 
  at Nereid.Client.Main (System.String[] args) [0x00000] 
  at (wrapper managed-to-native) System.AppDomain:ExecuteAssembly (System.Reflection.Assembly,string[])
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly a, System.String[] args) [0x00000] 
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string,System.Security.Policy.Evidence,string[])
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string)
  at Booter.Booter.BootClient (System.String clientName) [0x00000] 
  at Booter.Booter.Main () [0x00000] 

Unhandled Exception: System.DllNotFoundException: msvcrt
  at (wrapper managed-to-native) Mono.Unix.Native.Stdlib:free (intptr)
  at Mono.Unix.UnixMarshal.FreeHeap (IntPtr ptr) [0x00000] 
  at Mono.Unix.Catalog.GetString (System.String s) [0x00000] 
  at Hyena.Gui.Dialogs.ExceptionDialog.BuildExceptionMessage (System.Exception e) [0x00000] 
  at Hyena.Gui.Dialogs.ExceptionDialog..ctor (System.Exception e) [0x00000] 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup[Client] () [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup[Client] (System.String[] args) [0x00000] 
  at Nereid.Client.Main (System.String[] args) [0x00000] 
  at (wrapper managed-to-native) System.AppDomain:ExecuteAssembly (System.Reflection.Assembly,string[])
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly a, System.String[] args) [0x00000] 
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string,System.Security.Policy.Evidence,string[])
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string)
  at Booter.Booter.BootClient (System.String clientName) [0x00000] 
  at Booter.Booter.Main () [0x00000] 
```It looks like it's not finding a couple DLL's (msvcrt and intl). I get this output when running any banshee commands (banshee -h, --debug, etc.) 
I'd appreciate any help I can get.

Thanks,
Andrew

---

### Post by Padro89 on 2010-06-21
Hi!

I'm not completely sure if this will fix your problem but I guess you can try without danger.

There are two methods in the tutorial you mention and I don't know which is the one you followed, but each of them has its respective uninstall method. Why don't you undo what you did using one of the methods described there and then try to reinstall banshee?

If it doesn't work just try to uninstall banshee using

```
sudo apt-get remove banshee
```

I don't know if it'll work, but it won't do any harm so... let me know!

---

### Post by anfreita09 on 2010-06-21
I've tried that already, no luck :(

the tutorial I followed was the first one listed

---

### Post by Padro89 on 2010-06-21
You said you didn't finish the installation process. Where did you stop?

Maybe this is stupid but, have you tried with purge and autoremove instead of remove? If not, you should try (I understand 'purge' cleans some configuration files while 'remove' leaves them as they are).

I'd like to be more helpful, but this is the first time I hear about a dll library problem in linux (I thought dlls where from microsoft systems only) so if sudo apt-get purge banshee and sudo apt-get autoremove (and maybe, though I don't think it would make a big difference, erasing the .banshee folder in your home directory) does not solve it, I have no further ideas.

Sorry and good luck!

EDIT: You can also try sudo apt-get check to see if there are any broken dependencies.

---

### Post by anfreita09 on 2010-06-21
I stopped at the first line that wouldn't work, which would be:
```
svn co svn://svn.banshee-project.org/trunk/banshee-official-plugins
```
unfortunately autoremove, purge and check didn't work. I guess I'll just use rhythmbox for the time being. Thanks for your help

---

