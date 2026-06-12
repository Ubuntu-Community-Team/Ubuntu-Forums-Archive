---
title: "Amarok stopped working HELP"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by bward1 on 2007-01-07
I installed amarok about a week ago and have found it to be absolutely the best media player ever.  Unfortuneatly, I accidentally killed it and now I cant get it to work again.  I accidentally did rm -r .kde, since I dont use kde at all and things just haven't worked since then.  I have uninstalled kde and amarok (using both apt-get remove and synaptic) and apt-get update and apt-get upgrade and rebooted and anything and everything I could think of.  The first time after a reinstall the little config wizard comes up, but then it never boots up into the actual media player.  After that I dont even get the config wizard thing, and I just get this error message (when running from a terminal)

```
bward@Conroe:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use ama
p.
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

When I attempt to run it the splash screen i guess is what they call it comes up that says amarok, rediscover your music, fast forward, but I can't get to the actual media player.  What should I do?  Is there a more thorough way to uninstall so that i can reinstall and have it work like it did before?  Should I just try to install it myself from the source code?

---

### Post by Jussi Kukkonen on 2007-01-08
> Should I just try to install it myself from the source code?
No. Don't go there. In general it's smart to fix the problems before you go looking for new ones (amarok is a beast to compile)...

> Is there a more thorough way to uninstall so that i can reinstall and have it work like it did before? 
To remove everything, including the configuration files use "--purge":
```
apt-get remove --purge amarok
```

---

### Post by theoldgit on 2007-01-08
I am having similar problems. It workr=ed grat for me up until tonight. Mine does seem to go a bit further though. I have also found that if I run sudo amarok in a terminal it works fine. If not it opens so afar as when i try to add tracks to the playlist then just hangs forever. Running in terminal gives me this. -

```
mark@mark-desktop:~$ amarok
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
kbuildsycoca running...
amarok: BEGIN: void App::fixHyperThreading()
amarok:     Workaround not enabled
amarok: END__: void App::fixHyperThreading() - Took 0.00092s
amarok: END__: App::App() - Took 0.85s
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
amarok: END__: EngineBase* EngineController::loadEngine(const QString&) - Took 0.033s
amarok: BEGIN: CollectionDB::CollectionDB()
amarok: BEGIN: void CollectionDB::initialize()
amarok:       [ThreadWeaver] Creating pthread key, exit value is 0
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.011s
amarok: END__: void CollectionDB::initialize() - Took 0.079s
amarok:     [CollectionDB] INotify not available, using QTimer!
amarok: END__: CollectionDB::CollectionDB() - Took 0.12s
amarok: BEGIN: void CollectionDB::checkDatabase()
amarok:     [CollectionDB] INotify not available, using QTimer!
amarok: END__: void CollectionDB::checkDatabase() - Took 0.089s
amarok: BEGIN: MediaDeviceManager::MediaDeviceManager()
amarok: BEGIN: DeviceManager::DeviceManager()
amarok:       During DeviceManager init, error during DCOP call
amarok: BEGIN: Medium* DeviceManager::getDevice(QString)
amarok:         DeviceManager: getDevice called with name argument = init
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok:           Error during DCOP call
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.00075s
amarok: END__: Medium* DeviceManager::getDevice(QString) - Took 0.0011s
amarok:       DeviceManager:  connectDCOPSignal returned successfully!
amarok: END__: DeviceManager::DeviceManager() - Took 0.0041s
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok:       Error during DCOP call
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.00074s
amarok:     DeviceManager didn't return any devices, we are probably running on a non-KDE system. Trying to reinit media devices later
amarok: END__: MediaDeviceManager::MediaDeviceManager() - Took 0.0056s
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
amarok:         Error during DCOP call
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.00082s
amarok: END__: void MountPointManager::init() - Took 0.037s
amarok:     [Moodbar] Resetting moodbar:
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
amarok: BEGIN: Creating browsers. Please report long start times!
amarok: BEGIN: ContextBrowser
amarok: END__: ContextBrowser - Took 0.18s
amarok: BEGIN: CollectionBrowser
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.0006s
amarok:           [CollectionView::CollectionView(CollectionBrowser*)]
amarok:           current browser is not collection, aborting renderView()
amarok: END__: CollectionBrowser - Took 0.085s
amarok: BEGIN: PlaylistBrowser
amarok: BEGIN: PlaylistCategory* PlaylistBrowser::loadPodcasts()
amarok: END__: PlaylistCategory* PlaylistBrowser::loadPodcasts() - Took 0.021s
amarok: END__: PlaylistBrowser - Took 0.085s
amarok: BEGIN: FileBrowser
amarok: END__: FileBrowser - Took 0.59s
amarok:         [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 27 and [X-KDE-Amarok-plugintype] == 'mediadevice' and [X-KDE-Amarok-rank] > 0
amarok: BEGIN: MediaBrowser
amarok: END__: MediaBrowser - Took 0.023s
amarok: END__: Creating browsers. Please report long start times! - Took 1.2s
amarok: END__: void PlaylistWindow::init() - Took 1.8s
amarok: BEGIN: UrlLoader
amarok:       [KDE::ProgressBar::ProgressBar(QWidget*, QLabel*)]
amarok:       | Stamp: 1
amarok: BEGIN: void App::applySettings(bool)
amarok:         [Moodbar] Resetting moodbar:
amarok: BEGIN: EngineBase* EngineController::loadEngine()
amarok: BEGIN: EngineBase* EngineController::loadEngine(const QString&)
amarok:             [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 27 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] != 'xine-engine' and [X-KDE-Amarok-rank] > 0
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.0069s
amarok:             [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 27 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] == 'xine-engine' and [X-KDE-Amarok-rank] > 0
amarok:             [PluginManager] Trying to load: libamarok_xine-engine
amarok:             [xine-engine] hello
amarok:
amarok:             PluginManager Service Info:
amarok:             ---------------------------
amarok:             name                          : xine Engine
amarok:             library                       : libamarok_xine-engine
amarok:             desktopEntryPath              : amarok_xine-engine.desktop
amarok:             X-KDE-Amarok-plugintype       : engine
amarok:             X-KDE-Amarok-name             : xine-engine
amarok:             X-KDE-Amarok-authors          : (Max Howell)
amarok:             X-KDE-Amarok-rank             : 255
amarok:             X-KDE-Amarok-version          : 1
amarok:             X-KDE-Amarok-framework-version: 27
amarok:
amarok: BEGIN: virtual bool XineEngine::init()
amarok:               [xine-engine] 'Bringing joy to small mexican gerbils, a few weeks at a time.'
amarok:               [xine-engine] w00t/home/mark/.kde/share/apps/amarok/xine-config
amarok:               [xine-engine] gapless playback enabled.
amarok: END__: virtual bool XineEngine::init() - Took 0.31s
amarok: END__: EngineBase* EngineController::loadEngine(const QString&) - Took 0.48s
amarok: END__: EngineBase* EngineController::loadEngine() - Took 0.48s
amarok:         current browser is not collection, aborting renderView()
amarok: END__: void App::applySettings(bool) - Took 0.7s
amarok:       | Stamp: 2
amarok: BEGIN: ScriptManager::ScriptManager(QWidget*, const char*)
amarok: END__: ScriptManager::ScriptManager(QWidget*, const char*) - Took 0.0063s
amarok:       | Stamp: 3
mark@mark-desktop:~$ amarok:       [Moodbar] Resetting moodbar:
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 2s
amarok: BEGIN: ScanController::ScanController(CollectionDB*, bool, const QStringList&)
amarok: BEGIN: void ScanController::initIncremental()
amarok: BEGIN: virtual void UrlLoader::completeJob()
amarok: END__: virtual void UrlLoader::completeJob() - Took 0.00047s
amarok:         [ThreadWeaver] Job completed: UrlLoader. Jobs pending: 0
amarok: END__: UrlLoader - Took 1.2s
amarok:       [virtual KDE::ProgressBar::~ProgressBar()]
amarok:       [ThreadWeaver] Job completed: CurrentTrackJob. Jobs pending: 1
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.00072s
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: BEGIN: virtual bool StatisticsUpdateJob::doJob()
amarok:             [ScriptManager] Loaded: [LL] Lyriki
amarok:             [ScriptManager] Loaded: [LL] Lyrc
amarok:             [ScriptManager] Loaded: [LL] Leos Lyrics
amarok:             [ScriptManager] Loaded: [LL] LyricWiki
amarok:             [ScriptManager] Loaded: [LL] AZ Lyrics
amarok:             [ScriptManager] Loaded: [LL] Jamendo
amarok:             [ScriptManager] Loaded: [LL] Lyrix.at
amarok:             [ScriptManager] Loaded: [LL] Sing365
amarok:             [ScriptManager] Loaded: [LL] Terra Letras
amarok:             [ScriptManager] Loaded: playlist2html.py
amarok:             [ScriptManager] Loaded: PlaylistServer.py
amarok:             [ScriptManager] Loaded: Lyrc
amarok:             [ScriptManager] Loaded: Default
amarok:             [ScriptManager] Loaded: Impulsive
amarok:             [ScriptManager] Loaded: Web Control
amarok:             [ScriptManager] Auto-running script: Default
amarok:             [ScriptManager] Running script: /usr/share/apps/amarok/scripts/score_default/score_default.rb
amarok:             [ScriptManager] Auto-running script: [LL] Terra Letras
amarok:             [ScriptManager] Running script: /home/mark/.kde/share/apps/amarok/scripts/lyriki-lyrics/amarok_terraletras.rb
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok:               Error during DCOP call
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.015s
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.00099s
amarok:             [MountPointManager] Trying to update 27 statistics rows
amarok: END__: virtual bool StatisticsUpdateJob::doJob() - Took 0.36s
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.36s
amarok:         [ThreadWeaver] Job completed: StatisticsUpdateJob. Jobs pending: 0
amarok: END__: void ScanController::initIncremental() - Took 1.7s
amarok: END__: ScanController::ScanController(CollectionDB*, bool, const QStringList&) - Took 1.7s
amarok: END__: void App::continueInit() - Took 5.9s
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: BEGIN: virtual bool ScanController::doJob()
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.0013s
amarok: END__: virtual bool ScanController::doJob() - Took 0.0017s
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.0024s
amarok:   [CollectionDB] JobFinishedEvent from Incremental ScanController received.
amarok:   [ThreadWeaver] Job completed: CollectionScanner. Jobs pending: 0
amarok: BEGIN: virtual ScanController::~ScanController()
amarok: END__: virtual ScanController::~ScanController() - Took 0.00035s
amarok:   [ThreadWeaver] Job completed: CurrentTrackJob. Jobs pending: 0
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 1.6s
amarok: BEGIN: ScanController::ScanController(CollectionDB*, bool, const QStringList&)
amarok: BEGIN: void ScanController::initIncremental()
amarok: END__: void ScanController::initIncremental() - Took 0.077s
amarok: END__: ScanController::ScanController(CollectionDB*, bool, const QStringList&) - Took 0.077s
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: BEGIN: virtual bool ScanController::doJob()
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.0011s
amarok: END__: virtual bool ScanController::doJob() - Took 0.0013s
amarok:   [CollectionDB] JobFinishedEvent from Incremental ScanController received.
amarok:   [ThreadWeaver] Job completed: CollectionScanner. Jobs pending: 0
amarok: BEGIN: virtual ScanController::~ScanController()
amarok: END__: virtual ScanController::~ScanController() - Took 0.00015s
amarok: BEGIN: ScanController::ScanController(CollectionDB*, bool, const QStringList&)
amarok: BEGIN: void ScanController::initIncremental()
amarok: END__: void ScanController::initIncremental() - Took 0.07s
amarok: END__: ScanController::ScanController(CollectionDB*, bool, const QStringList&) - Took 0.07s
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.15s
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: BEGIN: virtual bool ScanController::doJob()
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.0013s
amarok: END__: virtual bool ScanController::doJob() - Took 0.0015s
amarok:   [CollectionDB] JobFinishedEvent from Incremental ScanController received.
amarok:   [ThreadWeaver] Job completed: CollectionScanner. Jobs pending: 0
amarok: BEGIN: virtual ScanController::~ScanController()
amarok: END__: virtual ScanController::~ScanController() - Took 0.00016s
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.018s

```

---

### Post by bward1 on 2007-01-08
Thanks for the advice, but that still isn't working.  I tried just about every option that seemed at all relevant in the apt-get man pages.  I did apt-get remove --purge and apt-get autoremove and apt-get clean and apt-get autoclean and then tried to reinstall after that.  I still receive the same error message after I install and it doesn't work.  I even deselected all of my third party sources in my sources.list file and it still doesn't work.  I get the same error message every time but I dont have a clue what is wrong with it.  Are there any other programs that I should uninstall to ensure that everything installs right, or that nothing is conflicting.  Is this the point where compiling myself is the best thing to do even though it is difficult?  Thanks for your help.

---

### Post by theoldgit on 2007-01-08
I found the problem for mine. I'll post it here in the hope it will work for you too.
Try removing the ~/.kde folder (To wastebasket so you can restore it).
If that wont work try removing ~/.xine (again to the wastebasket so you can restore it).

You will then have to tell Amorak where the music is, so be patient while that goes on. I hope this works as it did for me.

If these dont work, then put the two folders back and you will be back where you were.

---

