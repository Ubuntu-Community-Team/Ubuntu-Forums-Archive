---
title: "Amarok/gtkpod crashes on opening after updating iPod"
date: 2006-10-12
forum: Multimedia &amp; Video
---

### Post by csadowski on 2006-10-12
Hey guys, 

I updated the software on my iPod a few days ago, and now everytime i run amarok or gtkpod and they try to detect my ipod, they crash.  On gtkpod, I get a segmentation fault when running it thru terminal.  when Running amarok thru the terminal, I get:

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
amarok: BEGIN: App::App()
amarok: BEGIN: void App::fixHyperThreading()
amarok:     Workaround not enabled
amarok: END__: void App::fixHyperThreading() - Took 0.0009s
amarok: END__: App::App() - Took 0.012s
amarok: BEGIN: void App::continueInit()
amarok: BEGIN: EngineBase* EngineController::loadEngine(const QString&)
amarok:     [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 27 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] != 'void-engine' and [X-KDE-Amarok-rank] > 0
amarok:     [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 27 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] == 'void-engine' and [X-KDE-Amarok-rank] > 0
amarok:     [PluginManager] Trying to load: libamarok_void-engine_plugin
amarok:
amarok:     PluginManager Service Info:
amarok:     ---------------------------
amarok:     name                          : <no engine>
amarok:     library                       : libamarok_void-engine_plugin
amarok:     desktopEntryPath              : amarok_void-engine_plugin.desktop
amarok:     X-KDE-Amarok-plugintype       : engine
amarok:     X-KDE-Amarok-name             : void-engine
amarok:     X-KDE-Amarok-authors          : (Max Howell,Mark Kretschmann)
amarok:     X-KDE-Amarok-rank             : 1
amarok:     X-KDE-Amarok-version          : 1
amarok:     X-KDE-Amarok-framework-version: 27
amarok:
amarok: END__: EngineBase* EngineController::loadEngine(const QString&) - Took 0.071s
amarok: BEGIN: CollectionDB::CollectionDB()
amarok: BEGIN: void CollectionDB::initialize()
amarok:       [ThreadWeaver] Creating pthread key, exit value is 0
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.0014s
amarok: END__: void CollectionDB::initialize() - Took 0.084s
amarok:     [CollectionDB] INotify not available, using QTimer!
amarok: END__: CollectionDB::CollectionDB() - Took 0.12s
amarok: BEGIN: void CollectionDB::checkDatabase()
amarok:     [CollectionDB] INotify not available, using QTimer!
amarok: END__: void CollectionDB::checkDatabase() - Took 0.16s
amarok: BEGIN: MediaDeviceManager::MediaDeviceManager()
amarok: BEGIN: DeviceManager::DeviceManager()
amarok: BEGIN: Medium* DeviceManager::getDevice(QString)
amarok:         DeviceManager: getDevice called with name argument = init
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.00084s
amarok: END__: Medium* DeviceManager::getDevice(QString) - Took 0.0017s
amarok:       DeviceManager:  connectDCOPSignal returned successfully!
amarok: END__: DeviceManager::DeviceManager() - Took 0.0043s
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.00082s
amarok: BEGIN: void MediaDeviceManager::slotMediumAdded(const Medium*, QString)
amarok: END__: void MediaDeviceManager::slotMediumAdded(const Medium*, QString) - Took 0.00027s
amarok: BEGIN: void MediaDeviceManager::slotMediumAdded(const Medium*, QString)
amarok: END__: void MediaDeviceManager::slotMediumAdded(const Medium*, QString) - Took 0.00023s
amarok: BEGIN: void MediaDeviceManager::slotMediumAdded(const Medium*, QString)
amarok: END__: void MediaDeviceManager::slotMediumAdded(const Medium*, QString) - Took 0.003s
amarok: END__: MediaDeviceManager::MediaDeviceManager() - Took 0.011s
amarok: BEGIN: void PlaylistWindow::init()
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
amarok: BEGIN: void MountPointManager::init()
amarok:       [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 27 and [X-KDE-Amarok-plugintype] == 'device' and [X-KDE-Amarok-rank] > 0
amarok:       [MountPointManager] Received [3] device plugin offers
amarok:       [PluginManager] Trying to load: libamarok_massstorage-device
amarok:
amarok:       PluginManager Service Info:
amarok:       ---------------------------
amarok:       name                          : Mass Storage Device
amarok:       library                       : libamarok_massstorage-device
amarok:       desktopEntryPath              : amarok_massstorage-device.desktop
amarok:       X-KDE-Amarok-plugintype       : device
amarok:       X-KDE-Amarok-name             : massstorage-device
amarok:       X-KDE-Amarok-authors          : (Maximilian Kossick)
amarok:       X-KDE-Amarok-rank             : 100
amarok:       X-KDE-Amarok-version          : 1
amarok:       X-KDE-Amarok-framework-version: 27
amarok:
amarok:       [PluginManager] Trying to load: libamarok_smb-device
amarok:
amarok:       PluginManager Service Info:
amarok:       ---------------------------
amarok:       name                          : SMB Device
amarok:       library                       : libamarok_smb-device
amarok:       desktopEntryPath              : amarok_smb-device.desktop
amarok:       X-KDE-Amarok-plugintype       : device
amarok:       X-KDE-Amarok-name             : smb-device
amarok:       X-KDE-Amarok-authors          : (Maximilian Kossick)
amarok:       X-KDE-Amarok-rank             : 100
amarok:       X-KDE-Amarok-version          : 1
amarok:       X-KDE-Amarok-framework-version: 27
amarok:
amarok:       [PluginManager] Trying to load: libamarok_nfs-device
amarok:
amarok:       PluginManager Service Info:
amarok:       ---------------------------
amarok:       name                          : NFS Device
amarok:       library                       : libamarok_nfs-device
amarok:       desktopEntryPath              : amarok_nfs-device.desktop
amarok:       X-KDE-Amarok-plugintype       : device
amarok:       X-KDE-Amarok-name             : nfs-device
amarok:       X-KDE-Amarok-authors          : (Maximilian Kossick)
amarok:       X-KDE-Amarok-rank             : 100
amarok:       X-KDE-Amarok-version          : 1
amarok:       X-KDE-Amarok-framework-version: 27
amarok:
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.00054s
amarok: BEGIN: void MountPointManager::mediumChanged(const Medium*)
amarok: END__: void MountPointManager::mediumChanged(const Medium*) - Took 0.00025s
amarok: BEGIN: void MountPointManager::mediumChanged(const Medium*)
amarok:         [MountPointManager] found handler for /org/freedesktop/Hal/devices/volume_uuid_67e2c42b_e2e2_4abb_9547_25ac26602a7a
amarok:         [MassStorageDeviceHandler] Found existing UUID config for ID 1 , uuid /org/freedesktop/Hal/devices/volume_uuid_67e2c42b_e2e2_4abb_9547_25ac26602a7a
amarok:         [MountPointManager] added device 1 with mount point /
amarok: END__: void MountPointManager::mediumChanged(const Medium*) - Took 0.042s
amarok: BEGIN: void MountPointManager::mediumChanged(const Medium*)
amarok:         [MountPointManager] found handler for /org/freedesktop/Hal/devices/volume_uuid_7A519A1CCA2885ED
amarok:         [MassStorageDeviceHandler] Found existing UUID config for ID 4 , uuid /org/freedesktop/Hal/devices/volume_uuid_7A519A1CCA2885ED
amarok:         [MountPointManager] added device 4 with mount point /media/sda3
amarok: END__: void MountPointManager::mediumChanged(const Medium*) - Took 0.015s
amarok: END__: void MountPointManager::init() - Took 0.071s
amarok:     [Moodbar] Resetting moodbar:
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
amarok: BEGIN: Creating browsers. Please report long start times!
amarok: BEGIN: ContextBrowser
amarok: END__: ContextBrowser - Took 0.1s
amarok: BEGIN: CollectionBrowser
amarok:         [CollectionView::CollectionView(CollectionBrowser*)]
amarok:         current browser is not collection, aborting renderView()
amarok: END__: CollectionBrowser - Took 0.015s
amarok: BEGIN: PlaylistBrowser
amarok: BEGIN: PlaylistCategory* PlaylistBrowser::loadPodcasts()
amarok: END__: PlaylistCategory* PlaylistBrowser::loadPodcasts() - Took 0.0027s
amarok: END__: PlaylistBrowser - Took 0.014s
amarok: BEGIN: FileBrowser
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.00036s
ScimInputContextPlugin()
amarok: END__: FileBrowser - Took 0.37s
amarok:         [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 27 and [X-KDE-Amarok-plugintype] == 'mediadevice' and [X-KDE-Amarok-rank] > 0
amarok:         [MediaBrowser] mediumAdded: (true,/org/freedesktop/Hal/devices/volume_uuid_7A519A1CCA2885ED,sda3,MindJob,ipod,true,/dev/sda3,/media/sda3,hfsplus,true,,media/removable_mounted,ipod_mount)
amarok: BEGIN: MediaDevice* MediaBrowser::loadDevicePlugin(const QString&)
amarok: BEGIN: static amaroK::Plugin* PluginManager::createFromQuery(const QString&)
amarok:             [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 27 and [X-KDE-Amarok-plugintype] == 'mediadevice' and [X-KDE-Amarok-name] == 'ipod-mediadevice' and [X-KDE-Amarok-rank] > 0
amarok:             [PluginManager] Trying to load: libamarok_ipod-mediadevice
amarok:
amarok:             PluginManager Service Info:
amarok:             ---------------------------
amarok:             name                          : Apple iPod Media Device
amarok:             library                       : libamarok_ipod-mediadevice
amarok:             desktopEntryPath              : amarok_ipod-mediadevice.desktop
amarok:             X-KDE-Amarok-plugintype       : mediadevice
amarok:             X-KDE-Amarok-name             : ipod-mediadevice
amarok:             X-KDE-Amarok-authors          : (Martin Aumueller)
amarok:             X-KDE-Amarok-rank             : 100
amarok:             X-KDE-Amarok-version          : 1
amarok:             X-KDE-Amarok-framework-version: 27
amarok:
amarok: END__: static amaroK::Plugin* PluginManager::createFromQuery(const QString&) - Took 0.0097s
amarok:           [MediaBrowser] Returning plugin!
amarok: END__: MediaDevice* MediaBrowser::loadDevicePlugin(const QString&) - Took 0.012s
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 2.2s




and then it crashes.  It opens an email and tries to send the following error report:

Amarok has crashed! We are terribly sorry about this :(

But, all is not lost! You could potentially help us fix the crash. Information describing the crash is below, so just click send, or if you have time, write a brief description of how the crash happened first.

Many thanks.







The information below is to help the developers identify the problem, please do not modify it.



======== DEBUG INFORMATION  =======
Version:    1.4.3
Engine:     xine-engine
Build date: Sep 28 2006
CC version: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
KDElibs:    3.5.2
Qt:         3.3.6
TagLib:     1.4.0
CPU count:  1

==== file /usr/lib/amarok/amarokapp =======
/usr/lib/amarok/amarokapp: symbolic link to `/usr/bin/amarokapp'


==== (gdb) bt =====================
Using host libthread_db library "/lib/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread 46912614689568 (LWP 4677)]
0x00002aaaacad30ca in waitpid () from /lib/libpthread.so.0
#0  0x00002aaaacad30ca in waitpid () from /lib/libpthread.so.0
#1  0x00000000004059c4 in amaroK::Crash::crashHandler ()
#2  0x00002aaaad8eb1b0 in killpg () from /lib/libc.so.6
#3  0x0000000000000000 in ?? ()
#0  0x00002aaaacad30ca in waitpid () from /lib/libpthread.so.0
No symbol table info available.
#1  0x00000000004059c4 in amaroK::Crash::crashHandler ()
No symbol table info available.
#2  0x00002aaaad8eb1b0 in killpg () from /lib/libc.so.6
No symbol table info available.
#3  0x0000000000000000 in ?? ()
No symbol table info available.
==== (gdb) thread apply all bt ====
Thread 1 (Thread 46912614689568 (LWP 4677)):
#0  0x00002aaaacad30ca in waitpid () from /lib/libpthread.so.0
#1  0x00000000004059c4 in amaroK::Crash::crashHandler ()
#2  0x00002aaaad8eb1b0 in killpg () from /lib/libc.so.6
#3  0x0000000000000000 in ?? ()
#0  0x00002aaaacad30ca in waitpid () from /lib/libpthread.so.0


==== kdBacktrace() ================
[
0: /usr/lib/libkdecore.so.4(_Z11kdBacktracei+0x46) [0x2aaaabef46f6]
1: /usr/lib/libkdecore.so.4(_Z11kdBacktracev+0xe) [0x2aaaabef49ae]
2: amarok(_ZN6amaroK5Crash12crashHandlerEi+0xaec) [0x40544c]
3: /lib/libc.so.6 [0x2aaaad8eb1b0]
4: /lib/libc.so.6(strlen+0x10) [0x2aaaad92cfa0]
5: /usr/lib/libglib-2.0.so.0(g_strdup+0x23) [0x2aaab3544063]
6: /usr/lib/libgpod.so.0 [0x2aaab33fdba3]
7: /usr/lib/libgobject-2.0.so.0(g_object_newv+0x550) [0x2aaab37c25c0]
8: /usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x2af) [0x2aaab37c2c4f]
9: /usr/lib/libgobject-2.0.so.0(g_object_new+0xa1) [0x2aaab37c2df1]
10: /usr/lib/libgpod.so.0(itdb_device_new+0x1f) [0x2aaab33fc79f]
11: /usr/lib/libgpod.so.0(itdb_set_mountpoint+0x56) [0x2aaab33f4706]
12: /usr/lib/libgpod.so.0(itdb_parse+0x78) [0x2aaab33f5d98]
13: /usr/lib/kde3/libamarok_ipod-mediadevice.so(_ZN15IpodMediaDevice10openDeviceEb+0x55e) [0x2aaab32cb42e]
14: /usr/lib/libamarok.so.0(_ZN11MediaDevice13connectDeviceEb+0x88) [0x2aaaaaeb87d8]
15: /usr/lib/libamarok.so.0(_ZN12MediaBrowser9addDeviceEP11MediaDevice+0x90) [0x2aaaaaeb8d40]
16: /usr/lib/libamarok.so.0(_ZN12MediaBrowser11mediumAddedEPK6Medium7QStringb+0x19f) [0x2aaaaaeb9d1f]
17: /usr/lib/libamarok.so.0(_ZN12MediaBrowserC1EPKc+0x2201) [0x2aaaaaec4d31]
18: /usr/lib/libamarok.so.0(_ZN14PlaylistWindow4initEv+0x1c51) [0x2aaaaaf91241]
19: /usr/lib/libamarok.so.0(_ZN3App12continueInitEv+0x1c5) [0x2aaaaad8e925]
20: /usr/lib/libamarok.so.0(_ZN3App9qt_invokeEiP8QUObject+0xe2) [0x2aaaaad8f5e2]
21: /usr/lib/libqt-mt.so.3(_ZN7QObject15activate_signalEP15QConnectionListP8QUObject+0x12a) [0x2aaaadf0379e]
22: /usr/lib/libqt-mt.so.3(_ZN7QSignal6signalERK8QVariant+0x98) [0x2aaaae270ec0]
23: /usr/lib/libqt-mt.so.3(_ZN7QSignal8activateEv+0x6d) [0x2aaaadf20183]
24: /usr/lib/libqt-mt.so.3(_ZN16QSingleShotTimer5eventEP6QEvent+0x2c) [0x2aaaadf2725c]
25: /usr/lib/libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0x25e) [0x2aaaade9cc34]
26: /usr/lib/libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x258) [0x2aaaade9cea4]
27: /usr/lib/libkdecore.so.4(_ZN12KApplication6notifyEP7QObjectP6QEvent+0x19e) [0x2aaaabf79f6e]
28: /usr/lib/libqt-mt.so.3(_ZN12QApplication9sendEventEP7QObjectP6QEvent+0x58) [0x2aaaade2e36c]
29: /usr/lib/libqt-mt.so.3(_ZN10QEventLoop14activateTimersEv+0x224) [0x2aaaade8f17e]
30: /usr/lib/libqt-mt.so.3(_ZN10QEventLoop13processEventsEj+0xe0d) [0x2aaaade41b85]
31: /usr/lib/libqt-mt.so.3(_ZN10QEventLoop9enterLoopEv+0x66) [0x2aaaadeb4aca]
32: /usr/lib/libqt-mt.so.3(_ZN10QEventLoop4execEv+0x2f) [0x2aaaadeb49d3]
33: /usr/lib/libqt-mt.so.3(_ZN12QApplication4execEv+0x22) [0x2aaaade9b8a0]
34: amarok [0x40480c]
35: /lib/libc.so.6(__libc_start_main+0xdb) [0x2aaaad8d849b]
36: amarok [0x4041ca]
]












Any ideas as to whats going wrong and how I can fix it?

---

