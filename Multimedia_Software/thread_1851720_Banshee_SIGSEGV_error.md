---
title: "Banshee SIGSEGV error"
date: 2011-09-28
forum: Multimedia Software
---

### Post by NeethlingAD on 2011-09-28
So, I was just listening to music and banshee crashed. now i can't get it started again. removing and reinstalling fixes it-for a while. then it just crashes again. output from terminal:
Native stacktrace:

    banshee() [0x80dbc5b]
    banshee() [0x805e92f]
    [0x99e40c]
    /usr/lib/gstreamer-0.10/libgstflump3dec.so(+0x14aa3) [0x3812aa3]
    /usr/lib/gstreamer-0.10/libgstflump3dec.so(+0xc769) [0x380a769]
    /usr/lib/gstreamer-0.10/libgstflump3dec.so(+0x2f9a) [0x3800f9a]
    /usr/lib/gstreamer-0.10/libgstflump3dec.so(+0x47d7) [0x38027d7]
    /usr/lib/libgstreamer-0.10.so.0(gst_pad_push+0x210) [0x299b3a0]
    /usr/lib/gstreamer-0.10/libgstaudioparsersbad.so(+0x151c2) [0x4fdd1c2]
    /usr/lib/gstreamer-0.10/libgstaudioparsersbad.so(+0x15ee3) [0x4fddee3]
    /usr/lib/gstreamer-0.10/libgstaudioparsersbad.so(+0x190f3) [0x4fe10f3]
    /usr/lib/libgstreamer-0.10.so.0(+0x80bba) [0x29c4bba]
    /usr/lib/libgstreamer-0.10.so.0(+0x81ef7) [0x29c5ef7]
    /lib/i386-linux-gnu/libglib-2.0.so.0(+0x6ca39) [0x714a39]
    /lib/i386-linux-gnu/libglib-2.0.so.0(+0x6a2df) [0x7122df]
    /lib/i386-linux-gnu/libpthread.so.0(+0x5e99) [0x115e99]
    /lib/i386-linux-gnu/libc.so.6(clone+0x5e) [0x27773e]

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

previously I also got "SIGABRT while executing native code.", but this was fixed after removing and reinstalling. any help?

---

### Post by NeethlingAD on 2011-09-28
Okay, now it's back to the SIGABRT. new output from terminal:

ERROR:method-to-ir.c:11116:mono_spill_global_vars: assertion failed: (((sreg == -1) && (regtype == ' ')) || ((sreg != -1) && (regtype != ' ')))
Stacktrace:

Banshee.Configuration.Extensions.Get<System.DateTime> (Banshee.Configuration.IConfigurationClient,string,string,System.DateTime) <0x0003e>
  at Banshee.Configuration.Extensions.Get<System.DateTime> (Banshee.Configuration.IConfigurationClient,string,System.DateTime) <0x00034>
  at Banshee.CoverArt.CoverArtService.FetchCoverArt (bool) <0x000ca>
  at Banshee.CoverArt.CoverArtService.FetchCoverArt () <0x00049>
  at Banshee.CoverArt.CoverArtService.Initialize () <0x000ac>
  at Banshee.CoverArt.CoverArtService.ServiceStartup () <0x00024>
  at Banshee.CoverArt.CoverArtService.OnSourceAdded (Banshee.Sources.SourceAddedArgs) <0x00010>
  at (wrapper runtime-invoke) <Module>.runtime_invoke_void__this___object (object,intptr,intptr,intptr) <0x00046>
  at (wrapper managed-to-native) System.Reflection.MonoMethod.InternalInvoke (object,object[],System.Exception&) <0x00004>
  at (wrapper managed-to-native) System.Reflection.MonoMethod.InternalInvoke (object,object[],System.Exception&) <0x00004>
  at System.Reflection.MonoMethod.Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo) <0x0012a>
  at System.Reflection.MethodBase.Invoke (object,object[]) <0x00025>
  at System.Delegate.DynamicInvokeImpl (object[]) <0x0018a>
  at System.MulticastDelegate.DynamicInvokeImpl (object[]) <0x00034>
  at System.Delegate.DynamicInvoke (object[]) <0x00019>
  at Hyena.EventExtensions.SafeInvoke<object> (object,object[]) <0x000a1>
  at Banshee.Sources.SourceManager.AddSource (Banshee.Sources.Source,bool) <0x00251>
  at Banshee.ServiceStack.Application.Run () <0x00086>
  at Banshee.Gui.GtkBaseClient.Initialize (bool) <0x0027e>
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
  at Booter.Booter.Main () <0x001a0>
  at (wrapper runtime-invoke) object.runtime_invoke_void (object,intptr,intptr,intptr) <0x0003a>

Native stacktrace:

    banshee() [0x80dbc5b]
    [0x3f240c]
    /lib/i386-linux-gnu/libc.so.6(abort+0x17e) [0x16434e]
    /lib/i386-linux-gnu/libglib-2.0.so.0(g_assertion_message+0x150) [0xb053a0]
    /lib/i386-linux-gnu/libglib-2.0.so.0(+0x6897d) [0xb0597d]
    banshee() [0x809d865]
    banshee() [0x806145b]
    banshee() [0x8061f42]
    banshee() [0x8062ade]
    banshee() [0x80dcd40]
    [0x3d7066]
    [0x24ae7e7]
    [0x24ae7a2]
    [0x24ae718]
    [0xd2f5ba]
    [0xd2ef75]
    [0x24ae424]
    [0x24ae33f]
    [0x24ae2cd]
    [0x24ae123]
    [0x24ae042]
    [0x24adfe5]
    [0x23552c5]
    [0x24ade41]
    [0x24adedf]
    banshee() [0x8062bc8]
    banshee(mono_runtime_invoke+0x3e) [0x8192eee]
    banshee(mono_runtime_invoke_array+0x2a0) [0x81967a0]
    banshee() [0x814a098]
    [0xdad2e8]
    [0xdacddb]
    [0xdac91e]
    [0x61c094b]
    [0x61c07ad]
    [0x61c0772]
    [0xd429b2]
    [0xd42252]
    [0xc14faf]
    [0x3453ff]
    [0x3450f4]
    [0x3450b8]
    [0x345089]
    [0x2a4ff1]
    banshee() [0x8062bc8]
    banshee(mono_runtime_invoke+0x3e) [0x8192eee]
    banshee(mono_runtime_invoke_array+0x5c8) [0x8196ac8]
    banshee() [0x814a098]
    [0x2a4f18]
    [0x2a4b54]
    [0x2a49c0]
    [0x2a497b]
    [0x2a3685]
    [0x2a34eb]
    [0x345036]
    [0x344f02]
    [0x344e35]
    [0xdb5d61]
    [0xdb5bde]
    [0xdb5c34]
    banshee() [0x8062bc8]
    banshee(mono_runtime_invoke+0x3e) [0x8192eee]
    banshee(mono_runtime_exec_main+0xe0) [0x81959e0]
    [0xdb5b6f]
    [0xdb5a2f]
    [0xdb58fe]
    [0xdb58a8]
    [0xdb582a]
    [0xdb57e0]
    [0xdb55e2]
    [0x297351]
    [0x29744b]
    banshee() [0x8062bc8]
    banshee(mono_runtime_invoke+0x3e) [0x8192eee]
    banshee(mono_runtime_exec_main+0xe0) [0x81959e0]
    banshee(mono_runtime_run_main+0x11d) [0x8195ced]
    banshee(mono_main+0x1676) [0x80b7706]
    banshee() [0x8059355]
    /lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xe7) [0x14ce37]
    banshee() [0x8059291]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.

=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

---

