---
title: "Banshee will not start"
date: 2011-02-02
forum: Multimedia Software
---

### Post by cbrick77 on 2011-02-02
I've followed a ton of threads to try and get banshee to start but none have helped. Reinstalling mono-runtime didn't fix it neither did reinstalling Banshee itself.
 it repeats "at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>" for about a minute before getting to
```
at Mono.Addins.Serialization.BinaryXmlReader.SkipToValue (string) <0x00060>
  at Mono.Addins.Serialization.BinaryXmlReader.ReadStringValue (string) <0x00013>
  at Mono.Addins.Database.FileDatabase.OpenFileForPath (string,string,Mono.Addins.Serialization.BinaryXmlTypeMap,bool,object&) <0x00097>
  at Mono.Addins.Database.FileDatabase.ReadSharedObject (string,string,string,string,Mono.Addins.Serialization.BinaryXmlTypeMap,bool,string&) <0x00066>
  at Mono.Addins.Database.FileDatabase.ReadSharedObject (string,string,string,string,Mono.Addins.Serialization.BinaryXmlTypeMap,string&) <0x00021>
  at Mono.Addins.Database.AddinScanFolderInfo.Read (Mono.Addins.Database.FileDatabase,string,string) <0x00054>
  at Mono.Addins.Database.AddinDatabase.GetFolderInfoForPath (Mono.Addins.IProgressStatus,string,Mono.Addins.Database.AddinScanFolderInfo&) <0x0003d>
  at Mono.Addins.Database.AddinDatabase.GetFolderDomain (Mono.Addins.IProgressStatus,string) <0x0001e>
  at Mono.Addins.AddinRegistry..ctor (string,string) <0x000bb>
  at Mono.Addins.AddinManager.Initialize (string) <0x00107>
  at Banshee.ServiceStack.ServiceManager.InitializeAddins () <0x0003a>
  at Banshee.ServiceStack.ServiceManager.DefaultInitialize () <0x0000f>
  at Banshee.ServiceStack.Application.Initialize () <0x0000a>
  at Banshee.Gui.GtkBaseClient.Initialize (bool) <0x0003c>
  at Banshee.Gui.GtkBaseClient..ctor (bool,string) <0x00023>
  at Banshee.Gui.GtkBaseClient..ctor () <0x00017>
  at Nereid.Client..ctor () <0x00010>
  at (wrapper runtime-invoke) object.runtime_invoke_void__this__ (object,intptr,intptr,intptr) <0x00040>
  at (wrapper managed-to-native) System.Reflection.MonoCMethod.InternalInvoke (object,object[],System.Exception&) <0x00004>
  at (wrapper managed-to-native) System.Reflection.MonoCMethod.InternalInvoke (object,object[],System.Exception&) <0x00004>
  at System.Reflection.MonoCMethod.Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo) <0x0018b>
  at System.Reflection.MonoCMethod.Invoke (System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo) <0x00027>
  at System.Reflection.ConstructorInfo.Invoke (object[]) <0x00042>
  at System.Activator.CreateInstance (System.Type,bool) <0x00184>
  at System.Activator.CreateInstance (System.Type) <0x00012>
  at Banshee.Gui.GtkBaseClient.Startup () <0x00015>
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x00089>
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
  at Booter.Booter.Main () <0x0018a>
  at (wrapper runtime-invoke) object.runtime_invoke_void (object,intptr,intptr,intptr) <0x0003a>

Native stacktrace:

	banshee-1() [0x80d4d0b]
	banshee-1() [0x810ffeb]
	[0x9a440c]
	banshee-1() [0x81efebe]
	banshee-1() [0x81f13fd]
	banshee-1() [0x81b566e]
	[0xea5ac9]
	[0xea5a16]
	[0x1f6fbd7]
	[0x1f6fa1c]
	[0x1f6f911]
	[0x1f6fd5e]
	[0x1f6fd71]
```
and then repeats that "[0x1f6fd71]" for another minute or two until putting out the gdb dedug info:
```
Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================


```
I'm not sure what the problem is and I'd really like to get this working. I'm running Ubuntu 10.10 and trying to run Banshee 1.8.0

---

