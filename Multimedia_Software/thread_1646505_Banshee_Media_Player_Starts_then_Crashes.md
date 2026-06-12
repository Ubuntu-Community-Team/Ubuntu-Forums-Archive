---
title: "Banshee Media Player Starts then Crashes"
date: 2010-12-16
forum: Multimedia Software
---

### Post by Chris Donahoe on 2010-12-16
I'm running Ubuntu 10.04 LTS and recently upgraded Banshee Media Player which I had been using for months no problem. I'm not sure what version I was using before and I'm not sure what version I'm using now. I assume 1.8.0 or higher. Here's what I get when I type 'banshee' into the terminal:

[Info 13:12:49.932] Running Banshee 1.9.1: [Ubuntu 10.04.1 LTS d5f5788 (linux-gnu, i486) @ 2010-12-15 16:50:09 UTC]
[Warn 13:12:52.464] BansheeAwn - Failed loading Awn Extension. - System.Exception: org.freedesktop.DBus.Error.ServiceUnknown: The name com.google.code.Awn was not provided by any .service files (in `NDesk.DBus.Proxies')
at Banshee.Awn.IAvantWindowNavigatorProxy.UnsetTaskIc onByName (System.String TaskName) [0x00000]
at Banshee.Awn.AwnService.Banshee.ServiceStack.IExten sionService.Initialize () [0x00000]
[Info 13:12:52.534] Updating web proxy from GConf
[Info 13:12:52.594] All services are started 2.404954
[Info 13:12:53.607] nereid Client Started
[Info 13:12:53.927] AppleDeviceSource is ignoring unmounted volume sda3
[Warn 13:12:53.928] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceIn itialize (IDevice device) [0x00000]
at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000]
[Warn 13:12:53.936] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: s (in `mscorlib')
at System.Int32.Parse (System.String s) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.GetBusNumber (IUsbDevice device) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.get_BusNumber () [0x00000]
at Banshee.Hardware.Gio.Device.ResolveUsbPortInfo () [0x00000]
at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (IDevice device) [0x00000]
at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000]
[Warn 13:12:53.939] Caught an exception - System.ArgumentNullException: Argument cannot be null. (in `mscorlib')
at System.Int32.Parse (System.String s, NumberStyles style, IFormatProvider provider) [0x00000]
at System.Int32.Parse (System.String s, NumberStyles style) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.GetVendorId (IUsbDevice device) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.get_VendorId () [0x00000]
at Banshee.Dap.Karma.KarmaSource.IsKarma (IDevice dev) [0x00000]
at Banshee.Dap.Karma.KarmaSource.DeviceInitialize (IDevice dev) [0x00000]
at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000]
[Warn 13:12:54.021] Caught an exception - System.ArgumentNullException: Argument cannot be null. (in `mscorlib')
at System.Int32.Parse (System.String s, NumberStyles style, IFormatProvider provider) [0x00000]
at System.Int32.Parse (System.String s, NumberStyles style) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.GetVendorId (IUsbDevice device) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.get_VendorId () [0x00000]
at Banshee.Dap.MassStorage.DeviceMapper.Map (Banshee.Dap.MassStorage.MassStorageSource source) [0x00000]
at Banshee.Dap.MassStorage.MassStorageSource.DeviceIn itialize (IDevice device) [0x00000]
at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000]
[Info 13:12:54.022] AppleDeviceSource is ignoring unmounted volume sda2
[Warn 13:12:54.022] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceIn itialize (IDevice device) [0x00000]
at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000]
[Warn 13:12:54.023] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: s (in `mscorlib')
at System.Int32.Parse (System.String s) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.GetBusNumber (IUsbDevice device) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.get_BusNumber () [0x00000]
at Banshee.Hardware.Gio.Device.ResolveUsbPortInfo () [0x00000]
at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (IDevice device) [0x00000]
at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000]
[Warn 13:12:54.029] Caught an exception - System.ArgumentNullException: Argument cannot be null. (in `mscorlib')
at System.Int32.Parse (System.String s, NumberStyles style, IFormatProvider provider) [0x00000]
at System.Int32.Parse (System.String s, NumberStyles style) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.GetVendorId (IUsbDevice device) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.get_VendorId () [0x00000]
at Banshee.Dap.Karma.KarmaSource.IsKarma (IDevice dev) [0x00000]
at Banshee.Dap.Karma.KarmaSource.DeviceInitialize (IDevice dev) [0x00000]
at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000]
[Warn 13:12:54.030] Caught an exception - System.ArgumentNullException: Argument cannot be null. (in `mscorlib')
at System.Int32.Parse (System.String s, NumberStyles style, IFormatProvider provider) [0x00000]
at System.Int32.Parse (System.String s, NumberStyles style) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.GetVendorId (IUsbDevice device) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.get_VendorId () [0x00000]
at Banshee.Dap.MassStorage.DeviceMapper.Map (Banshee.Dap.MassStorage.MassStorageSource source) [0x00000]
at Banshee.Dap.MassStorage.MassStorageSource.DeviceIn itialize (IDevice device) [0x00000]
at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000]
[Info 13:12:54.100] AppleDeviceSource is ignoring unmounted volume sda1
[Warn 13:12:54.100] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceIn itialize (IDevice device) [0x00000]
at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000]
[Warn 13:12:54.104] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: s (in `mscorlib')
at System.Int32.Parse (System.String s) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.GetBusNumber (IUsbDevice device) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.get_BusNumber () [0x00000]
at Banshee.Hardware.Gio.Device.ResolveUsbPortInfo () [0x00000]
at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (IDevice device) [0x00000]
at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000]
[Warn 13:12:54.105] Caught an exception - System.ArgumentNullException: Argument cannot be null. (in `mscorlib')
at System.Int32.Parse (System.String s, NumberStyles style, IFormatProvider provider) [0x00000]
at System.Int32.Parse (System.String s, NumberStyles style) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.GetVendorId (IUsbDevice device) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.get_VendorId () [0x00000]
at Banshee.Dap.Karma.KarmaSource.IsKarma (IDevice dev) [0x00000]
at Banshee.Dap.Karma.KarmaSource.DeviceInitialize (IDevice dev) [0x00000]
at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000]
[Warn 13:12:54.105] Caught an exception - System.ArgumentNullException: Argument cannot be null. (in `mscorlib')
at System.Int32.Parse (System.String s, NumberStyles style, IFormatProvider provider) [0x00000]
at System.Int32.Parse (System.String s, NumberStyles style) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.GetVendorId (IUsbDevice device) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.get_VendorId () [0x00000]
at Banshee.Dap.MassStorage.DeviceMapper.Map (Banshee.Dap.MassStorage.MassStorageSource source) [0x00000]
at Banshee.Dap.MassStorage.MassStorageSource.DeviceIn itialize (IDevice device) [0x00000]
at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000]
[Warn 13:12:54.121] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: s (in `mscorlib')
at System.Int32.Parse (System.String s) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.GetBusNumber (IUsbDevice device) [0x00000]
at Banshee.Hardware.Gio.UsbDevice.get_BusNumber () [0x00000]
at Banshee.Hardware.Gio.Device.ResolveUsbPortInfo () [0x00000]
at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (IDevice device) [0x00000]
at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000]
Exception in Gtk# callback delegate
Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.IndexOutOfRangeException: Array index is out of range.
at Hyena.Widgets.SimpleTable`1[Banshee.Dap.DapLibrarySync].InsertRow (Banshee.Dap.DapLibrarySync item, UInt32 row, Gtk.Widget[] cols) [0x00000]
at Hyena.Widgets.SimpleTable`1[Banshee.Dap.DapLibrarySync].AddRow (Banshee.Dap.DapLibrarySync item, Gtk.Widget[] cols) [0x00000]
at Banshee.Dap.Gui.DapContent.AddLibrary (Banshee.Dap.DapLibrarySync library_sync) [0x00000]
at Banshee.Dap.Gui.DapContent.BuildWidgets () [0x00000]
at Banshee.Dap.Gui.DapContent..ctor (Banshee.Dap.DapSource source) [0x00000]
at Banshee.Dap.DapSource.<Initialize>m__F () [0x00000]
at Banshee.ServiceStack.Application+<Invoke>c__AnonSt orey27.<>m__43 () [0x00000]
at Banshee.Gui.GtkBaseClient+<RunIdle>c__AnonStorey1D .<>m__9F () [0x00000]
at GLib.Idle+IdleProxy.Handler () [0x00000]
at GLib.ExceptionManager.RaiseUnhandledException(Syst em.Exception e, Boolean is_terminal)
at GLib.Idle+IdleProxy.Handler()
at Gtk.Application.gtk_main()
at Gtk.Application.Run()
at Banshee.Gui.GtkBaseClient.Run()
at Banshee.Gui.GtkBaseClient.Startup()
at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.Start upInvocationHandler startup)
at Banshee.Gui.GtkBaseClient.Startup()
at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
at Nereid.Client.Main(System.String[] args)
at System.AppDomain.ExecuteAssembly(System.Reflection .Assembly , System.String[] )
at System.AppDomain.ExecuteAssemblyInternal(System.Re flection.Assembly a, System.String[] args)
at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
at Booter.Booter.BootClient(System.String clientName)
at Booter.Booter.Main()
Chris Donahoe is offline   	Reply With Quote

---

### Post by Chris Donahoe on 2010-12-16
Update: The player only crashes when I have my external harddrive mounted. Banshee will open and stay open as long as I don't have my HD mounted. As soon as I mount it, the program crashes.

---

### Post by Chris Donahoe on 2010-12-16
solved:

[http://ubuntu-ky.ubuntuforums.org/sh....php?t=1629453](http://ubuntu-ky.ubuntuforums.org/sh....php?t=1629453)

---

### Post by Chris Donahoe on 2010-12-18
Sorry, this did not solve the problem. I think it is a problem related to cpu usage. Please help!!

---

### Post by Joseph Schwenker on 2011-01-06
I just had a similar problem when I booted my system with a flash drive mounted.  Banshee crashed with this output until I unmounted the flash drive.  Perhaps Banshee is trying to read the device as an external audio player?  I'll see if disabling some external audio player-related plugins helps.

```
joseph@joseph:~$ banshee
[Info  15:58:42.374] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-11-26 13:53:04 UTC]
[Info  15:58:43.362] Updating web proxy from GConf
[Info  15:58:43.401] All services are started 0.839907
[Info  15:58:44.086] nereid Client Started
[Warn  15:58:44.228] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: s (in `mscorlib')
  at System.Int32.Parse (System.String s) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.UsbDevice.GetBusNumber (IUsbDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.UsbDevice.get_BusNumber () [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.Device.ResolveUsbPortInfo () [0x00000] in <filename unknown>:0 
  at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 
Stacktrace:

  at (wrapper managed-to-native) System.Net.Dns.GetHostByName_internal (string,string&,string[]&,string[]&) <0x00004>
  at (wrapper managed-to-native) System.Net.Dns.GetHostByName_internal (string,string&,string[]&,string[]&) <0x00004>
  at System.Net.Dns.GetHostByName (string) <0x00038>
  at System.Net.ServicePoint.get_HostEntry () <0x00137>
  at System.Net.WebConnection.Connect (System.Net.HttpWebRequest) <0x0010b>
  at System.Net.WebConnection.InitConnection (object) <0x00129>
  at (wrapper runtime-invoke) object.runtime_invoke_void__this___object (object,intptr,intptr,intptr) <0x00046>

Native stacktrace:

	banshee-1() [0x80d4d0b]
	banshee-1() [0x810ffeb]
	[0xb774d40c]
	/lib/libnss_wins.so.2(_nss_wins_gethostbyname2_r+0x3f) [0xa8da161f]
	/lib/libc.so.6(gethostbyname2_r+0x1c5) [0xb759c1a5]
	/lib/libc.so.6(+0xa782c) [0xb755b82c]
	/lib/libc.so.6(getaddrinfo+0x165) [0xb755d3b5]
	banshee-1() [0x8158c93]
	[0xa915c4e3]
	[0xa915c401]
	[0xa915c220]
	[0xa915bc5c]
	[0xa915b922]
	[0xb67ee0bf]
	banshee-1() [0x8061328]
	banshee-1(mono_runtime_invoke+0x40) [0x813c890]
	banshee-1(mono_runtime_invoke_array+0x2a4) [0x81421a4]
	banshee-1() [0x814266e]
	banshee-1() [0x81d2341]
	banshee-1() [0x81d2858]
	banshee-1() [0x81b11db]
	banshee-1() [0x81e8e4e]
	banshee-1() [0x8214f85]
	/lib/libpthread.so.0(+0x5cc9) [0xb763ccc9]
	/lib/libc.so.6(clone+0x5e) [0xb758469e]

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

Aborted

```

Also, Banshee only crashed after I played a few specific songs.  When I played one song, it crashed, but when I played another, it stayed open.

---

### Post by war59312 on 2011-02-06
I get this crash when clicking on Amazon MP3 Store or Micro Guide :

> will@will-linux-laptop:~$ banshee --debug
** Running Mono with --debug   **
[1 Info  02:35:03.530] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-11-26 13:53:04 UTC]
[1 Debug 02:35:03.550] Initializing GTK
[1 Debug 02:35:05.285] Post-Initializing GTK
[1 Debug 02:35:05.307] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[1 Debug 02:35:05.323] Using default gconf-base-key
[1 Debug 02:35:05.355] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[1 Debug 02:35:05.438] Core service started (DBusServiceManager, 0.001367)
[1 Debug 02:35:05.440] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[1 Debug 02:35:05.450] Core service started (DBusCommandService, 0.011642)
[1 Debug 02:35:05.530] Opened SQLite (version 3.7.2) connection to /home/will/.config/banshee-1/banshee.db
[1 Debug 02:35:05.531] Core service started (DbConnection, 0.080753)
[1 Debug 02:35:05.535] Database version 43 is up to date
[1 Debug 02:35:05.560] Core service started (PreferenceService, 0.00875)
[1 Debug 02:35:05.568] Core service started (Network, 0.007113)
[1 Debug 02:35:05.568] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[1 Debug 02:35:05.568] Core service started (SourceManager, 0.000665)
[1 Debug 02:35:05.579] Core service started (MediaProfileManager, 0.000229)
[1 Debug 02:35:05.584] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[1 Debug 02:35:05.586] Core service started (PlayerEngine, 0.006151)
[1 Debug 02:35:05.604] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[1 Debug 02:35:05.605] Core service started (PlaybackController, 0.002993)
[1 Debug 02:35:05.614] Starting - Startup Job
[1 Debug 02:35:05.615] Core service started (JobScheduler, 0.009832)
[1 Debug 02:35:05.635] IO provider extension loaded (Banshee.IO.Gio.Provider)
[1 Debug 02:35:05.673] Loaded HardwareManager backend: Banshee.Hardware.Gio
[1 Debug 02:35:05.675] Core service started (HardwareManager, 0.060059)
[1 Debug 02:35:05.677] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[1 Debug 02:35:05.679] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[1 Debug 02:35:05.681] Core service started (CollectionIndexerService, 0.005834)
[1 Debug 02:35:05.683] Core service started (SaveTrackMetadataService, 0.001891)
[1 Debug 02:35:05.693] Adding icon theme search path: /usr/share/banshee-1/icons
[1 Debug 02:35:05.694] Core service started (GtkElementsService, 0.010774)
[1 Debug 02:35:05.695] Core service started (InterfaceActionService, 0.001494)
[1 Debug 02:35:05.809] Extension actions loaded: MetadataFixActions
[1 Debug 02:35:05.810] Registering remote object /org/bansheeproject/Banshee/GlobalUIActions (Banshee.Gui.GlobalActions) on org.bansheeproject.Banshee
[1 Debug 02:35:05.811] Album artwork path set to /home/will/.cache/media-art
[1 Debug 02:35:05.835] Core service started (ArtworkManager, 0.025234)
[1 Debug 02:35:05.835] Core service started (BookmarksService, 0.000158)
[1 Debug 02:35:06.031] Adding context page lastfm-recommendations
[1 Debug 02:35:06.053] Adding context page wikipedia
[1 Debug 02:35:06.336] Constructed Nereid interface: 0.473942
[1 Debug 02:35:06.410] Creating new surface cache for 90px images, capped at 0.62 MiB (20 items)
[1 Debug 02:35:06.460] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[1 Debug 02:35:06.460] Core service started (NereidPlayerInterface, 0.624677)
[1 Debug 02:35:06.487] Extension service started (GStreamerCoreService, 0.026507)
[1 Debug 02:35:06.495] Extension service started (BpmService, 0.007638)
[1 Debug 02:35:06.499] Using GNOME 2.22 API for Multimedia Keys
[1 Debug 02:35:06.499] Extension service started (MultimediaKeysService, 0.003655)
[1 Debug 02:35:06.516] Audioscrobbler state: connected
[1 Debug 02:35:06.518] Extension service started (AudioscrobblerService, 0.019352)
[1 Debug 02:35:06.520] Extension service started (LibraryWatcherService, 0.001523)
[1 Debug 02:35:06.522] Extension service started (PodcastService, 0.00261)
[1 Debug 02:35:06.524] Extension service started (DapService, 0.001401)
[1 Info  02:35:06.527] Updating web proxy from GConf
[1 Debug 02:35:06.532] Direct connection, no proxy in use
[1 Debug 02:35:06.551] Extension service started (GnomeService, 0.026674)
[1 Debug 02:35:06.552] Extension service started (DaapService, 0.00131)
[1 Debug 02:35:06.558] Extension service started (AmazonMp3DownloaderService, 0.006045)
[1 Debug 02:35:06.618] Extension service started (NotificationAreaService, 0.060026)
[1 Debug 02:35:06.620] Extension service started (CoverArtService, 0.001947)
[1 Debug 02:35:06.647] Extension service started (AudioCdService, 0.026641)
[1 Info  02:35:06.648] All services are started 1.291359
[1 Debug 02:35:07.051] Registering remote object /org/bansheeproject/Banshee/SourceManager/PlayQueue (Banshee.PlayQueue.PlayQueueSource) on org.bansheeproject.Banshee
[1 Debug 02:35:07.052] Extension source loaded: Play Queue
[1 Debug 02:35:07.073] Extension source loaded: Last.fm
[1 Debug 02:35:07.079] Extension source loaded: Now Playing
[1 Debug 02:35:07.096] Extension source loaded: Radio
[1 Debug 02:35:07.107] Extension source loaded: File System Queue
[1 Debug 02:35:07.123] Extension source loaded: Amazon MP3 Store
[1 Debug 02:35:07.130] Extension source loaded: Miro Guide
[1 Debug 02:35:07.142] Extension source loaded: Internet Archive
[1 Debug 02:35:07.168] Extension source loaded: Audiobooks, etc
[1 Debug 02:35:07.173] Starting GTK main loop
[1 Debug 02:35:07.196] Growing surface cache for 90px images to 0.99 MiB (32 items)
[1 Debug 02:35:07.296] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 02:35:07.354] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 02:35:07.371] Creating Pango.Layout, configuring Cairo.Context
[1 Info  02:35:07.483] nereid Client Started
[1 Debug 02:35:07.486] Delayed Initializating Banshee.MediaEngine.PlayerEngineService
[1 Debug 02:35:07.492] (libbanshee:player) Stream volume supported: YES
[1 Debug 02:35:07.494] (libbanshee:player) Audiosink has volume: NO
[1 Debug 02:35:07.497] (libbanshee:player) Using system (gst-plugins-good) equalizer element
[1 Debug 02:35:07.552] Player state change: NotReady -> Ready
[1 Debug 02:35:07.556] Loaded equalizer presets: 0.00016
[1 Debug 02:35:07.560] Selected equalizer: Rock
[1 Debug 02:35:07.565] Player state change: Ready -> Idle
[1 Debug 02:35:07.569] (libbanshee:player) Disabled ReplayGain
[1 Debug 02:35:07.574] Delayed Initializating Banshee.LibraryWatcher.LibraryWatcherService
[1 Debug 02:35:07.585] Core service started (LibraryImportManager, 0.006438)
[1 Debug 02:35:07.622] Started LibraryWatcher for Music (/home/will/Music/)
[1 Debug 02:35:07.624] Started LibraryWatcher for Videos (/home/will/Videos/)
[1 Debug 02:35:07.630] Starting
[1 Debug 02:35:07.650] Delayed Initializating Banshee.Podcasting.PodcastService
[1 Debug 02:35:07.748] Delayed Initializating Banshee.Dap.DapService
[1 Debug 02:35:07.754] Dap support extension loaded: Banshee.Dap.MassStorage
[1 Debug 02:35:07.755] Dap support extension loaded: Banshee.Dap.Karma
[1 Debug 02:35:07.756] Dap support extension loaded: Banshee.Dap.AppleDevice
[1 Debug 02:35:07.757] Dap support extension loaded: Banshee.Dap.Mtp
[1 Debug 02:35:07.762] Delayed Initializating Banshee.Daap.DaapService
[2 Debug 02:35:07.765] Refreshing any podcasts that haven't been updated in over an hour
[3 Info  02:35:07.829] AppleDeviceSource is ignoring unmounted volume System Reserved
[3 Warn  02:35:07.849] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 
[4 Debug 02:35:07.854] Encountered a problem processing: file:///home/will/Videos/fsi.rhpot1080-3.avi
[4 Warn  02:35:07.854] Caught an exception - TagLib.CorruptFileException: File does not begin with RIFF identifier (in `taglib-sharp')
  at TagLib.Riff.File.Read (Boolean read_tags, ReadStyle style, System.UInt32& riff_size, System.Int64& tag_start, System.Int64& tag_end) [0x00000] in <filename unknown>:0 
  at TagLib.Riff.File..ctor (IFileAbstraction abstraction, ReadStyle propertiesStyle) [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
[3 Info  02:35:07.885] AppleDeviceSource is ignoring unmounted volume 138 GB Filesystem
[3 Warn  02:35:07.885] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 
[4 Debug 02:35:07.893] Finished - Rescanning 1 of 1
[4 Debug 02:35:07.897] Finished - Rescanning 1 of 1
[5 Debug 02:35:07.993] DAAP Proxy listening for connections on port 8089
[1 Debug 02:35:08.773] Finished - Startup Job
Stacktrace:

  at (wrapper managed-to-native) System.Net.Dns.GetHostByName_internal (string,string&,string[]&,string[]&) <0x00004>
  at (wrapper managed-to-native) System.Net.Dns.GetHostByName_internal (string,string&,string[]&,string[]&) <0x00004>
  at System.Net.Dns.GetHostByName (string) <IL 0x00018, 0x00038>
  at System.Net.ServicePoint.get_HostEntry () <IL 0x000a6, 0x00137>
  at System.Net.WebConnection.Connect (System.Net.HttpWebRequest) <IL 0x00086, 0x0010b>
  at System.Net.WebConnection.InitConnection (object) <IL 0x0003f, 0x00129>
  at (wrapper runtime-invoke) object.runtime_invoke_void__this___object (object,intptr,intptr,intptr) <IL 0x0001e, 0x00046>

Native stacktrace:

    banshee-1() [0x80d4d0b]
    banshee-1() [0x810ffeb]
    [0x83e40c]
    /lib/libnss_wins.so.2(_nss_wins_gethostbyname2_r+0x3f) [0x648e61f]
    /lib/libc.so.6(gethostbyname2_r+0x1c5) [0xaee1a5]
    /lib/libc.so.6(+0xa782c) [0xaad82c]
    /lib/libc.so.6(getaddrinfo+0x165) [0xaaf3b5]
    banshee-1() [0x8158c93]
    [0x3866d43]
    [0x3866c61]
    [0x3866a80]
    [0x386610c]
    [0x38658a2]
    [0x20d0bf]
    banshee-1() [0x8061328]
    banshee-1(mono_runtime_invoke+0x40) [0x813c890]
    banshee-1(mono_runtime_invoke_array+0x2a4) [0x81421a4]
    banshee-1() [0x814266e]
    banshee-1() [0x81d2341]
    banshee-1() [0x81d2858]
    banshee-1() [0x81b11db]
    banshee-1() [0x81e8e4e]
    banshee-1() [0x8214f85]
    /lib/libpthread.so.0(+0x5cc9) [0xda7cc9]
    /lib/libc.so.6(clone+0x5e) [0xad669e]

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

Aborted
And when I try to play any file, I get this crash:

> will@will-linux-laptop:~$ banshee --debug
** Running Mono with --debug   **
[1 Info  02:37:04.529] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-11-26 13:53:04 UTC]
[1 Debug 02:37:04.549] Initializing GTK
[1 Debug 02:37:06.005] Post-Initializing GTK
[1 Debug 02:37:06.028] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[1 Debug 02:37:06.042] Using default gconf-base-key
[1 Debug 02:37:06.076] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[1 Debug 02:37:06.159] Core service started (DBusServiceManager, 0.001367)
[1 Debug 02:37:06.161] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[1 Debug 02:37:06.171] Core service started (DBusCommandService, 0.011725)
[1 Debug 02:37:06.251] Opened SQLite (version 3.7.2) connection to /home/will/.config/banshee-1/banshee.db
[1 Debug 02:37:06.252] Core service started (DbConnection, 0.080932)
[1 Debug 02:37:06.257] Database version 43 is up to date
[1 Debug 02:37:06.284] Core service started (PreferenceService, 0.009948)
[1 Debug 02:37:06.290] Core service started (Network, 0.006384)
[1 Debug 02:37:06.291] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[1 Debug 02:37:06.291] Core service started (SourceManager, 0.000689)
[1 Debug 02:37:06.300] Core service started (MediaProfileManager, 0.000228)
[1 Debug 02:37:06.307] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[1 Debug 02:37:06.309] Core service started (PlayerEngine, 0.008747)
[1 Debug 02:37:06.328] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[1 Debug 02:37:06.329] Core service started (PlaybackController, 0.003112)
[1 Debug 02:37:06.337] Starting - Startup Job
[1 Debug 02:37:06.338] Core service started (JobScheduler, 0.009595)
[1 Debug 02:37:06.359] IO provider extension loaded (Banshee.IO.Gio.Provider)
[1 Debug 02:37:06.396] Loaded HardwareManager backend: Banshee.Hardware.Gio
[1 Debug 02:37:06.398] Core service started (HardwareManager, 0.059835)
[1 Debug 02:37:06.401] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[1 Debug 02:37:06.402] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[1 Debug 02:37:06.404] Core service started (CollectionIndexerService, 0.005906)
[1 Debug 02:37:06.406] Core service started (SaveTrackMetadataService, 0.001761)
[1 Debug 02:37:06.416] Adding icon theme search path: /usr/share/banshee-1/icons
[1 Debug 02:37:06.417] Core service started (GtkElementsService, 0.010727)
[1 Debug 02:37:06.418] Core service started (InterfaceActionService, 0.001616)
[1 Debug 02:37:06.531] Extension actions loaded: MetadataFixActions
[1 Debug 02:37:06.532] Registering remote object /org/bansheeproject/Banshee/GlobalUIActions (Banshee.Gui.GlobalActions) on org.bansheeproject.Banshee
[1 Debug 02:37:06.533] Album artwork path set to /home/will/.cache/media-art
[1 Debug 02:37:06.558] Core service started (ArtworkManager, 0.02608)
[1 Debug 02:37:06.558] Core service started (BookmarksService, 0.000157)
[1 Debug 02:37:06.749] Adding context page lastfm-recommendations
[1 Debug 02:37:06.771] Adding context page wikipedia
[1 Debug 02:37:07.057] Constructed Nereid interface: 0.473294
[1 Debug 02:37:07.132] Creating new surface cache for 90px images, capped at 0.62 MiB (20 items)
[1 Debug 02:37:07.192] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[1 Debug 02:37:07.192] Core service started (NereidPlayerInterface, 0.634343)
[1 Debug 02:37:07.219] Extension service started (GStreamerCoreService, 0.025954)
[1 Debug 02:37:07.227] Extension service started (BpmService, 0.007343)
[1 Debug 02:37:07.230] Using GNOME 2.22 API for Multimedia Keys
[1 Debug 02:37:07.230] Extension service started (MultimediaKeysService, 0.003602)
[1 Debug 02:37:07.247] Audioscrobbler state: connected
[1 Debug 02:37:07.249] Extension service started (AudioscrobblerService, 0.018447)
[1 Debug 02:37:07.251] Extension service started (LibraryWatcherService, 0.001617)
[1 Debug 02:37:07.253] Extension service started (PodcastService, 0.002461)
[1 Debug 02:37:07.254] Extension service started (DapService, 0.001113)
[1 Info  02:37:07.258] Updating web proxy from GConf
[1 Debug 02:37:07.262] Direct connection, no proxy in use
[1 Debug 02:37:07.280] Extension service started (GnomeService, 0.025209)
[1 Debug 02:37:07.281] Extension service started (DaapService, 0.001064)
[1 Debug 02:37:07.283] Extension service started (AmazonMp3DownloaderService, 0.001883)
[1 Debug 02:37:07.326] Extension service started (NotificationAreaService, 0.043585)
[1 Debug 02:37:07.328] Extension service started (CoverArtService, 0.002009)
[1 Debug 02:37:07.355] Extension service started (AudioCdService, 0.026475)
[1 Info  02:37:07.356] All services are started 1.278372
[1 Debug 02:37:07.757] Registering remote object /org/bansheeproject/Banshee/SourceManager/PlayQueue (Banshee.PlayQueue.PlayQueueSource) on org.bansheeproject.Banshee
[1 Debug 02:37:07.757] Extension source loaded: Play Queue
[1 Debug 02:37:07.775] Extension source loaded: Last.fm
[1 Debug 02:37:07.781] Extension source loaded: Now Playing
[1 Debug 02:37:07.794] Extension source loaded: Radio
[1 Debug 02:37:07.806] Extension source loaded: File System Queue
[1 Debug 02:37:07.813] Extension source loaded: Amazon MP3 Store
[1 Debug 02:37:07.821] Extension source loaded: Miro Guide
[1 Debug 02:37:07.833] Extension source loaded: Internet Archive
[1 Debug 02:37:07.860] Extension source loaded: Audiobooks, etc
[1 Debug 02:37:07.864] Starting GTK main loop
[1 Debug 02:37:07.893] Growing surface cache for 90px images to 0.99 MiB (32 items)
[1 Debug 02:37:08.001] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 02:37:08.061] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 02:37:08.078] Creating Pango.Layout, configuring Cairo.Context
[1 Info  02:37:08.189] nereid Client Started
[1 Debug 02:37:08.193] Delayed Initializating Banshee.MediaEngine.PlayerEngineService
[1 Debug 02:37:08.198] (libbanshee:player) Stream volume supported: YES
[1 Debug 02:37:08.200] (libbanshee:player) Audiosink has volume: NO
[1 Debug 02:37:08.204] (libbanshee:player) Using system (gst-plugins-good) equalizer element
[1 Debug 02:37:08.257] Player state change: NotReady -> Ready
[1 Debug 02:37:08.262] Loaded equalizer presets: 0.000162
[1 Debug 02:37:08.266] Selected equalizer: Rock
[1 Debug 02:37:08.271] Player state change: Ready -> Idle
[1 Debug 02:37:08.275] (libbanshee:player) Disabled ReplayGain
[1 Debug 02:37:08.280] Delayed Initializating Banshee.LibraryWatcher.LibraryWatcherService
[1 Debug 02:37:08.290] Core service started (LibraryImportManager, 0.006284)
[1 Debug 02:37:08.334] Started LibraryWatcher for Music (/home/will/Music/)
[1 Debug 02:37:08.335] Started LibraryWatcher for Videos (/home/will/Videos/)
[1 Debug 02:37:08.345] Starting
[1 Debug 02:37:08.367] Delayed Initializating Banshee.Podcasting.PodcastService
[1 Debug 02:37:08.452] Delayed Initializating Banshee.Dap.DapService
[1 Debug 02:37:08.458] Dap support extension loaded: Banshee.Dap.MassStorage
[1 Debug 02:37:08.459] Dap support extension loaded: Banshee.Dap.Karma
[1 Debug 02:37:08.460] Dap support extension loaded: Banshee.Dap.AppleDevice
[1 Debug 02:37:08.461] Dap support extension loaded: Banshee.Dap.Mtp
[1 Debug 02:37:08.467] Delayed Initializating Banshee.Daap.DaapService
[2 Debug 02:37:08.473] Refreshing any podcasts that haven't been updated in over an hour
[3 Info  02:37:08.519] AppleDeviceSource is ignoring unmounted volume System Reserved
[3 Warn  02:37:08.536] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 
[4 Debug 02:37:08.560] Encountered a problem processing: file:///home/will/Videos/fsi.rhpot1080-3.avi
[4 Warn  02:37:08.561] Caught an exception - TagLib.CorruptFileException: File does not begin with RIFF identifier (in `taglib-sharp')
  at TagLib.Riff.File.Read (Boolean read_tags, ReadStyle style, System.UInt32& riff_size, System.Int64& tag_start, System.Int64& tag_end) [0x00000] in <filename unknown>:0 
  at TagLib.Riff.File..ctor (IFileAbstraction abstraction, ReadStyle propertiesStyle) [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
[3 Info  02:37:08.574] AppleDeviceSource is ignoring unmounted volume 138 GB Filesystem
[3 Warn  02:37:08.574] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 
[4 Debug 02:37:08.587] Finished - Rescanning 1 of 1
[4 Debug 02:37:08.591] Finished - Rescanning 1 of 1
[5 Debug 02:37:08.722] DAAP Proxy listening for connections on port 8089
[1 Debug 02:37:09.469] Finished - Startup Job
[1 Debug 02:37:09.829] Player state change: Idle -> Loading
[1 Debug 02:37:09.858] Loaded IScreensaverManager: Banshee.GnomeBackend.GnomeScreensaverManager
[1 Debug 02:37:09.983] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 02:37:09.983] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 02:37:10.014] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 02:37:10.014] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 02:37:10.014] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 02:37:10.339] Player state change: Loading -> Loaded
[1 Debug 02:37:10.349] (libbanshee:player) [gapless] Triggering track-change signal
[6 Debug 02:37:10.364] Encountered a problem processing: file:///home/will/Videos/fsi.rhpot1080-3.avi
[6 Warn  02:37:10.364] Caught an exception - TagLib.CorruptFileException: File does not begin with RIFF identifier (in `taglib-sharp')
  at TagLib.Riff.File.Read (Boolean read_tags, ReadStyle style, System.UInt32& riff_size, System.Int64& tag_start, System.Int64& tag_end) [0x00000] in <filename unknown>:0 
  at TagLib.Riff.File..ctor (IFileAbstraction abstraction, ReadStyle propertiesStyle) [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
[1 Debug 02:37:10.402] Player state change: Loaded -> Playing
[6 Warn  02:37:10.411] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: input (in `System')
  at System.Text.RegularExpressions.Regex.Replace (System.String input, System.String replacement, Int32 count, Int32 startat) [0x00000] in <filename unknown>:0 
  at System.Text.RegularExpressions.Regex.Replace (System.String input, System.String replacement) [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.Rhapsody.RhapsodyQueryJob.EscapeUrlPart (System.String part) [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.Rhapsody.RhapsodyQueryJob.GetAlbumUrl (IBasicTrackInfo track) [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.Rhapsody.RhapsodyQueryJob.Run () [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.MetadataServiceJob.Run () [0x00000] in <filename unknown>:0 
Stacktrace:

  at (wrapper managed-to-native) System.Net.Dns.GetHostByName_internal (string,string&,string[]&,string[]&) <0x00004>
  at (wrapper managed-to-native) System.Net.Dns.GetHostByName_internal (string,string&,string[]&,string[]&) <0x00004>
  at System.Net.Dns.GetHostByName (string) <IL 0x00018, 0x00038>
  at System.Net.ServicePoint.get_HostEntry () <IL 0x000a6, 0x00137>
  at System.Net.WebConnection.Connect (System.Net.HttpWebRequest) <IL 0x00086, 0x0010b>
  at System.Net.WebConnection.InitConnection (object) <IL 0x0003f, 0x00129>
  at (wrapper runtime-invoke) object.runtime_invoke_void__this___object (object,intptr,intptr,intptr) <IL 0x0001e, 0x00046>

Native stacktrace:

    banshee-1() [0x80d4d0b]
    banshee-1() [0x810ffeb]
    [0xb8240c]
    /lib/libnss_wins.so.2(_nss_wins_gethostbyname2_r+0x3f) [0xa5cf661f]
    /lib/libc.so.6(gethostbyname2_r+0x1c5) [0xac41a5]
    /lib/libc.so.6(+0xa782c) [0xa8382c]
    /lib/libc.so.6(getaddrinfo+0x165) [0xa853b5]
    banshee-1() [0x8158c93]
    [0x3782033]
    [0x3781f51]
    [0x3781d70]
    [0x37817ac]
    [0x3781472]
    [0x8970bf]
    banshee-1() [0x8061328]
    banshee-1(mono_runtime_invoke+0x40) [0x813c890]
    banshee-1(mono_runtime_invoke_array+0x2a4) [0x81421a4]
    banshee-1() [0x814266e]
    banshee-1() [0x81d2341]
    banshee-1() [0x81d2858]
    banshee-1() [0x81b11db]
    banshee-1() [0x81e8e4e]
    banshee-1() [0x8214f85]
    /lib/libpthread.so.0(+0x5cc9) [0xb3fcc9]
    /lib/libc.so.6(clone+0x5e) [0xaac69e]

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

Aborted


---

### Post by war59312 on 2011-02-15
Bump, anyone?

---

