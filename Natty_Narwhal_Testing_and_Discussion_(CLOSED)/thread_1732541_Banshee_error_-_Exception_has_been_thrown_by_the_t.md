---
title: "Banshee error - Exception has been thrown by the target of an invocation."
date: 2011-04-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2011-04-18
I got this error today .Banshee wont start at all.

```
[Info  18:57:14.303] Running Banshee 2.0.0: [Ubuntu Natty (development branch) (linux-gnu, x86_64) @ 2011-04-09 07:44:31 UTC]
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

---

### Post by gnomeuser on 2011-04-18
This is a known bug, occasionally you can get around it by running with --debug-addins once. I can't remember the bug number of hand but if you encounter more problems please read this:

[http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/](http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/)

*edit*
[https://bugzilla.gnome.org//show_bug.cgi?id=647412](https://bugzilla.gnome.org//show_bug.cgi?id=647412)

---

### Post by rajeev1204 on 2011-04-18
> **gnomeuser said:**
> This is a known bug, occasionally you can get around it by running with --debug-addins once. I can't remember the bug number of hand but if you encounter more problems please read this:

[http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/](http://www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/)

*edit*
[https://bugzilla.gnome.org//show_bug.cgi?id=647412](https://bugzilla.gnome.org//show_bug.cgi?id=647412)


Tried the debug addins line with a sudo and banshee starts.Do you want me to add something to that bug report? Seems like all the required logs are already there.

---

