---
title: "Amarok issues"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by tater_3001 on 2006-11-11
Ok when i open amarok it shows the splashcscreen and then quits, its not in the tray either... when i run it from teminal i get this:
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
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
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
amarok: BEGIN: App::App()
amarok: BEGIN: void App::fixHyperThreading()
amarok:     Workaround not enabled
amarok: END__: void App::fixHyperThreading() - Took 0.0011s
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
amarok: END__: EngineBase* EngineController::loadEngine(const QString&) - Took 0.095s
amarok: BEGIN: CollectionDB::CollectionDB()
amarok: BEGIN: void CollectionDB::initialize()
amarok:       [ThreadWeaver] Creating pthread key, exit value is 0
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.0019s
amarok: END__: void CollectionDB::initialize() - Took 0.11s
amarok:     [CollectionDB] INotify not available, using QTimer!
amarok: END__: CollectionDB::CollectionDB() - Took 0.13s
amarok: BEGIN: void CollectionDB::checkDatabase()
amarok:     [CollectionDB] Beginning database update
amarok:     [CollectionDB] Different database stats version detected! Stats table will be updated or rebuilt.
amarok:     [CollectionDB] [ERROR!] Database statistics version too new for this version of Amarok. Quitting...
amarok: BEGIN: virtual CollectionDB::~CollectionDB()
amarok:       [CollectionDB] Running VACUUM
amarok: END__: virtual CollectionDB::~CollectionDB() - Took 0.092s
amarok:     [virtual EngineController::~EngineController()]

and ya if you can help i could sure use it haha thanks, Turner

---

### Post by chriscando on 2006-11-11
It says 'failed to open device' are you trying to sync it with an ipod or anything? Also, I wonder if you would get the same errors if you ran it as root.

---

### Post by tater_3001 on 2006-11-11
nope not tryin to sync with anything unless its tryin to sync with my usb xbox controller... ill try as root Thanks, Turner

---

### Post by tater_3001 on 2006-11-11
Ha running as root worked, but it is still giving me the bad device messages.. ill try unhooking my usb controller
thanks, Turner

---

### Post by chriscando on 2006-11-11
Did it ever work for you or is the first time you are trying to get it working? If this problem just occured out of nowhere and you dont mind losing (possibly) all of your amarok settings, you might try deleteing the directory ~/.kde/share/apps/amarok maybe this will 'fix' your current settings. You could always cp the directory somewhere else as a backup.

---

### Post by chriscando on 2006-11-11
Hmm, if it worked as root its probably your directory (~/.kde/share/apps/amarok)
When you ran as root were all your normal settings intact? If not it probably setup a new account for root. Which suggests there is something wrong with your current user's settings.

---

### Post by tater_3001 on 2006-11-11
kk ill try that, and ya it came from nowhere, it worked fine for like 3 weeks then just quit on me today haha thanks, Turner

---

### Post by tater_3001 on 2006-11-12
kk i did that but it still doesnt work... o/w i can get used to sudo ing it 
haha Thanks anyway, Turner

---

### Post by tater_3001 on 2006-11-14
haha i downloaded songbird to fix the problem... amarok still doesnt work but songbird is just as good... :P

---

