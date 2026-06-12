---
title: "Banshee 1.7.5 crashing on start"
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by rogerdean on 2010-09-08
Morning all

Is anyone else seeing the newly updated banshee 1.7.5 crashing on start? If so I'll file a bug

```
roger@roger-laptop:~$ banshee
[Info  08:51:06.386] Running Banshee 1.7.5: [Ubuntu maverick (development branch) (linux-gnu, i686) @ 2010-09-07 19:18:43 UTC]
[Info  08:51:08.162] Updating web proxy from GConf
[Info  08:51:08.218] All services are started 1.49409
[Info  08:51:09.360] nereid Client Started
[Warn  08:51:09.592] Caught an exception - System.DllNotFoundException: libglib-2.0.dll (in `gkeyfile-sharp')
  at (wrapper managed-to-native) KeyFile.GKeyFile:g_key_file_new ()
  at KeyFile.GKeyFile..ctor () [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.DeviceMediaCapabilities+GMpiFileInfo..ctor (System.String mediaPlayerId) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.DeviceMediaCapabilities..ctor (Banshee.Hardware.Gio.RawDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.RawVolume.get_MediaCapabilities () [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.Device.get_MediaCapabilities () [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService+MapDeviceJob.Run () [0x00000] in <filename unknown>:0 
[Warn  08:51:09.594] Caught an exception - System.DllNotFoundException: libglib-2.0.dll (in `gkeyfile-sharp')
  at (wrapper managed-to-native) KeyFile.GKeyFile:g_key_file_new ()
  at KeyFile.GKeyFile..ctor () [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.DeviceMediaCapabilities+GMpiFileInfo..ctor (System.String mediaPlayerId) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.DeviceMediaCapabilities..ctor (Banshee.Hardware.Gio.RawDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.RawVolume.get_MediaCapabilities () [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.Device.get_MediaCapabilities () [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService+MapDeviceJob.Run () [0x00000] in <filename unknown>:0 
[Warn  08:51:09.595] Caught an exception - System.DllNotFoundException: libglib-2.0.dll (in `gkeyfile-sharp')
  at (wrapper managed-to-native) KeyFile.GKeyFile:g_key_file_new ()
  at KeyFile.GKeyFile..ctor () [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.DeviceMediaCapabilities+GMpiFileInfo..ctor (System.String mediaPlayerId) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.DeviceMediaCapabilities..ctor (Banshee.Hardware.Gio.RawDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.RawVolume.get_MediaCapabilities () [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.Device.get_MediaCapabilities () [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService+MapDeviceJob.Run () [0x00000] in <filename unknown>:0 
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.DllNotFoundException: libglib-2.0.dll
  at (wrapper managed-to-native) KeyFile.GKeyFile:g_key_file_free (intptr)
  at KeyFile.GKeyFile+FinalizerInfo.Handler () [0x00000] in <filename unknown>:0 
  at GLib.Timeout+TimeoutProxy.Handler () [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Timeout+TimeoutProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Banshee.Gui.GtkBaseClient.Run()
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
roger@roger-laptop:~$ 

```

---

### Post by macstevejb on 2010-09-08
I have Banshee 1.7.4 but as of this morning it too is crashing on startup

---

### Post by macstevejb on 2010-09-08
oops correction on that...upgraded to 1.7.5 and with a new rash of updates this morning, Banshee now starts up fine
:p

---

### Post by rogerdean on 2010-09-08
Hmmm... i've just done a clean install from the daily image and installed 1.7.5 - no crash. All well then. I was expecting this release to work with the sound indicator, but no sign on that yet
R

---

### Post by nperry on 2010-09-08
Obtain debug information:

Quit banshee

run: banshee-1 –debug –redirect-log

Reproduce your problem and exit Banshee

then a log can be found in ~/.config/banshee-1/log – then create a new bug report in launchpad.

---

### Post by jrd on 2010-09-08
I had the same problem. I ended up downgrading banshee until the new updates came through (within a few hours it seems), then I upgraded to 1.7.5 again and now it works fine. So my suggestion is to make sure you are updated all the way. 

BTW: If you end up downgrading you have to delete (or rename) your ~./config/banshee-1/banshee.db file since it is not compatible with the old one.

---

