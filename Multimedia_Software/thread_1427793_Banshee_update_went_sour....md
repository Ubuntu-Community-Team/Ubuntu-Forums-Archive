---
title: "Banshee update went sour..."
date: 2010-03-12
forum: Multimedia Software
---

### Post by Enigmapond on 2010-03-12
Hi,

I just received an update to banshee 1.5.5-1 and where would normally be a good thing, seems it won't even start now and was working just perfectly up until the update. Anyone else having this problem? Any suggestions? I tried re-installing with the same results and won't start through the terminal either...
I get -
```
[Info  00:30:32.180] Running Banshee 1.5.5: [Ubuntu 9.04 (linux-gnu, i486) @ 2010-03-11 20:40:45 UTC]
[Info  00:30:36.857] All services are started 3.934464s
Marshaling changed signal
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetException: Object does not match target type.
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] 
  at System.Delegate.DynamicInvokeImpl (System.Object[] args) [0x00000] 
  at System.MulticastDelegate.DynamicInvokeImpl (System.Object[] args) [0x00000] 
  at System.Delegate.DynamicInvoke (System.Object[] args) [0x00000] 
  at GLib.Signal.ClosureInvokedCB (System.Object o, GLib.ClosureInvokedArgs args) [0x00000] 
  at GLib.SignalClosure.Invoke (GLib.ClosureInvokedArgs args) [0x00000] 
  at GLib.SignalClosure.MarshalCallback (IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.ComboBox.gtk_combo_box_set_active_iter(IntPtr , IntPtr )
   at Gtk.ComboBox.SetActiveIter(TreeIter iter)
   at Banshee.Widgets.DictionaryComboBox`1[[Banshee.Collection.Database.RandomBy, Banshee.Services, Version=1.5.0.0, Culture=neutral, PublicKeyToken=null]].set_ActiveValue(Banshee.Collection.Database.RandomBy value)
   at Banshee.PlayQueue.HeaderWidget..ctor(Banshee.Collection.Database.Shuffler shuffler, System.String shuffle_mode_id, System.String source_name)
   at Banshee.PlayQueue.PlayQueueSource.CreateHeaderWidget()
   at Banshee.PlayQueue.PlayQueueSource.Initialize()
   at Banshee.PlayQueue.PlayQueueSource..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
   at Mono.Addins.TypeExtensionNode.CreateInstance()
   at Banshee.Sources.SourceManager.OnExtensionChanged(System.Object o, Mono.Addins.ExtensionNodeEventArgs args)
   at Mono.Addins.ExtensionNode.add_ExtensionNodeChanged(Mono.Addins.ExtensionNodeEventHandler value)
   at Mono.Addins.ExtensionContext.AddExtensionNodeHandler(System.String path, Mono.Addins.ExtensionNodeEventHandler handler)
   at Mono.Addins.AddinManager.AddExtensionNodeHandler(System.String path, Mono.Addins.ExtensionNodeEventHandler handler)
   at Banshee.Sources.SourceManager.LoadExtensionSources()
   at Banshee.ServiceStack.Application.Run()
   at Banshee.Gui.GtkBaseClient.Initialize(Boolean registerCommonServices)
   at Banshee.Gui.GtkBaseClient..ctor(Boolean initializeDefault, System.String defaultIconName)
   at Banshee.Gui.GtkBaseClient..ctor()
   at Nereid.Client..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
   at Nereid.Client.Main(System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()
```
And then it just closes...

---

### Post by Enigmapond on 2010-03-12
bump..:confused:

---

### Post by yanbab on 2010-03-12
same here :(
(ubuntu jaunty, banshee from ppa)

---

### Post by ptha on 2010-03-12
Same issue, same exception message when I launch Banshee from the console. I had just configured the Update Manager to get the latest PPA, and installed the latest version, upgrading from 1.4.3 to 1.5.5.

---

### Post by Enigmapond on 2010-03-12
Yes well that's what broke my Banshee and I still haven't been able to fix it. Anyway to just roll it back? I got the upgrade right from the lastest PPA....I'm at a loss.

---

### Post by bedhead75 on 2010-03-12
[http://ubuntuforums.org/showthread.php?t=1427778](http://ubuntuforums.org/showthread.php?t=1427778)

Try removing the mirage plugin from the repos.

---

### Post by Enigmapond on 2010-03-12
Thanks but...I didn't even have that installed.

---

### Post by Enigmapond on 2010-03-12
Ran a debug and have attached the result...HELP BANSHEE TEAM!!! Please don't make me remove this wonderful programme....

---

### Post by Enigmapond on 2010-03-13
So that's it? I'm doomed until Lucid???

---

### Post by wimpelmeesje on 2010-03-14
I'm having the exact same problem. Hopefully a fix will be out soon :/.

---

### Post by dr_dred5 on 2010-03-14
Same here, but I had been tweaking it and assumed it was something I'd done.

Has anyone filed a bug report with the developers?

---

### Post by Enigmapond on 2010-03-14
I am not familiar with filing a bug report..I tried but I got a 500 error when apport tried to send it. I looked at the PPA and none were filed. I also added the "daily-build" PPA but got no updates.

---

### Post by oimon on 2010-03-16
suffering with the same problem after update to 1.5.5. ubuntu seriously needs a rollback feature to stop this kind of thing happening.

---

### Post by m4dm4n on 2010-03-17
Until they fix this, if you want to revert to the functioning version in the Jaunty repos you could try Package > Force version in Synaptic and select the 1.4 one.

---

### Post by oier on 2010-03-17
I have the same problem. I am also using Jaunty and the banshee's team PPA.
Downgrading to 1.4 worked fine.

---

### Post by nicjasno on 2010-03-18
Same problem here, i'm eager to see if this will be fixed before 10.04 .

---

### Post by Enigmapond on 2010-03-19
> **m4dm4n said:**
> Until they fix this, if you want to revert to the functioning version in the Jaunty repos you could try Package > Force version in Synaptic and select the 1.4 one.

Thanks for the tip. I was unaware that could be done and now my banshee works again..:D Cheers for that! BOOO to the broken one..;)

---

### Post by Quake on 2010-03-19
Thank you m4dm4n!!! I was having the same problem!

---

### Post by jonnylinuxnerd on 2010-03-20
I had the exact same problem on jaunty and also had to downgrade, I'm guessing somewhere the dependencies are messed up or sumit :(

---

### Post by boombox1387 on 2010-03-20
Are all people who ran into this bug trying to upgrade from the 1.4 series to 1.5.5?  I follow Banshee bug reports pretty closely, and I haven't heard of this issue until now.  This seems pretty serious, and it also seems to be affecting a lot of people.  If you're experiencing this issue, please consider filing a bug report against the Banshee project.  You can do this on Launchpad, but for a more direct route to the Banshee developers, please follow the instructions here: banshee-project.org/contribute/file-bugs/

---

### Post by Enigmapond on 2010-03-20
Thank you. I just filed a bug report. There were no others that I found.;)

---

### Post by Enigmapond on 2010-03-20
I just got word from the developer that the problem has been fixed and upon the next upgrade to 1.5.6, (probably in the next couple of days), it will right itself...YAY! Nice work Banshee Team!! Thank You!!

---

### Post by boombox1387 on 2010-03-20
> **Enigmapond said:**
> I just got word from the developer that the problem has been fixed and upon the next upgrade to 1.5.6, (probably in the next couple of days), it will right itself...YAY! Nice work Banshee Team!! Thank You!!

Glad your issue is fixed!  Sorry I didn't catch that before I told you to go report the bug. :)  Sounds like 1.5.6 should be released pretty soon (today or tomorrow), so I hope everything works for you once that happens.

---

### Post by jonnylinuxnerd on 2010-03-23
Just updated to 1.5.6 and it fixed all the problems! Yay! :D Thanks banshee team for fixing so quickly!

---

### Post by Cuppa-Chino on 2010-03-23
1.5.6 on lucid is not working for me, just so you know -- will try to debug and pass the bug up the chain.
actually I just needed to delete most things in my .config/banshee folder and the mirage extension

---

### Post by m4dm4n on 2010-03-28
I was getting a weird error about "Could not read add-in description" for a while but it was fixed by deleting ~/.config/banshee-1/addin-db-001 and starting from scratch. I don't know if anyone else is having this issue because I fiddled around with a couple of builds before the 1.5.6 fix was released.

---

