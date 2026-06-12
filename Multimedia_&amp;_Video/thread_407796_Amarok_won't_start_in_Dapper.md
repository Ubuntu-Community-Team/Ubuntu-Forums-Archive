---
title: "Amarok won't start in Dapper"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by notoriousdbp on 2007-04-12
Yesterday I re-installed Dapper.  I went through the usual routes of getting codecs installed etc and installed Amarok as it is my preferred music player for mp3 streams from [www.di.fm](www.di.fm).  However, I can't get it to start at all.  When I first ran it there was a box popped up on screen which said something about being unable to find any sound engines (I have xine, also and all the gstreamer plugins installed) but couldn't read anything else as it was covered by the amarok splash screen.  I've tried completely removing amarok and re-installing and have even installed kubuntu-desktop in case it was a KDE library issue.

When I run amarok from the command line this is the output:

> X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
amarok: BEGIN: App::App()
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
amarok: BEGIN: void App::fixHyperThreading()
amarok:     Workaround not enabled
amarok: END__: void App::fixHyperThreading() - Took 0.00066s
amarok: END__: App::App() - Took 0.73s
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
amarok: END__: EngineBase* EngineController::loadEngine(const QString&) - Took 0.054s
amarok: BEGIN: CollectionDB::CollectionDB()
amarok: BEGIN: void CollectionDB::initialize()
amarok:       [ThreadWeaver] Creating pthread key, exit value is 0
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.0011s
amarok: END__: void CollectionDB::initialize() - Took 0.033s
amarok:     [CollectionDB] INotify not available, using QTimer!
amarok: END__: CollectionDB::CollectionDB() - Took 0.045s
amarok: BEGIN: void CollectionDB::checkDatabase()
amarok:     [CollectionDB] Beginning database update
amarok:     [CollectionDB] [ERROR!] There is a bug in Amarok: instead of destroying your valuable database tables, I'm quitting
amarok: BEGIN: virtual CollectionDB::~CollectionDB()
amarok:       [CollectionDB] Running VACUUM
amarok: END__: virtual CollectionDB::~CollectionDB() - Took 0.047s
amarok:     [virtual EngineController::~EngineController()]


Can anyone help me get it running?

---

### Post by becominglumberg on 2007-04-13
If I had to guess, I would say that the KDElibs that Amarok has to have are hosed. I would try reinstalling KDElibs and then Amarok to see if that makes things happier.

---

