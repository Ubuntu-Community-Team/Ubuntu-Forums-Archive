---
title: "Cannot close Amarok"
date: 2010-07-16
forum: Multimedia Software
---

### Post by alt126 on 2010-07-16
Hi,

I have a Dell New Studio 17 with Ubuntu 10.4 x64.

I can open Amarok and works fine, but when i close the app this does not dissapear from the task bar...and the process still there...

```
antonio@antonio-portatil:~$ amarok
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
amarok(3476)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(3476)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(3476)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
Calling appendChild() on a null node does nothing.
QGraphicsLinearLayout::removeAt: invalid index 1
amarok(3476)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(3476)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
role  0  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QString, "Playlist Files on Disk") ,  QVariant(QString, "Internal Database") )  ) 
role  1  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QIcon, ) ,  QVariant(QIcon, ) )  ) 
role  3  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QString, "Playlist Files on Disk") ,  QVariant(QString, "Internal Database") )  ) 
QMap((0, QMap((0, QVariant(QString, "Playlist Files on Disk") ) ( 1 ,  QVariant(QIcon, ) ) ( 3 ,  QVariant(QString, "Playlist Files on Disk") ) )  ) )  
Creating empty group:  "Playlist Files on Disk" 
QMap((0, QMap((0, QVariant(QString, "Internal Database") ) ( 1 ,  QVariant(QIcon, ) ) ( 3 ,  QVariant(QString, "Internal Database") ) )  ) )  
Creating empty group:  "Internal Database" 
QMap() 
amarok(3476)/kdeui (Wallet): The kwalletd service has been disabled 
amarok(3476)/kdeui (Wallet): The kwalletd service has been disabled 
amarok(3476)/kdeui (Wallet): The kwalletd service has been disabled 
amarok(3476)/kdeui (Wallet): The kwalletd service has been disabled 
amarok(3476)/kdeui (Wallet): The kwalletd service has been disabled 
amarok(3476)/kdeui (Wallet): The kwalletd service has been disabled 
role  0  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QString, "Local Podcasts") )  ) 
role  1  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QIcon, ) )  ) 
role  3  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QString, "Local Podcasts") )  ) 
QMap((0, QMap((0, QVariant(QString, "Local Podcasts") ) ( 1 ,  QVariant(QIcon, ) ) ( 3 ,  QVariant(QString, "Local Podcasts") ) )  ) )  
Creating empty group:  "Local Podcasts" 
amarok(3476)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Amarok Script Console"
amarok(3476)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "LyricWiki"
amarok(3476)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Cool Streams"
amarok(3476)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Librivox.org"
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x4000024
amarok:  ********************************************************************************************** 
amarok:  ** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: ** 
amarok:  ** amarok --debug                                                                           ** 
amarok:  ********************************************************************************************** 
antonio@antonio-portatil:~$ QVariantMap DBusMenuExporterDBus::GetProperties(int, const QStringList&): Condition failed: action
```

```
antonio@antonio-portatil:~$ amarok --debug
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
amarok(2795)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(2795)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(2795)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
Calling appendChild() on a null node does nothing.
QGraphicsLinearLayout::removeAt: invalid index 1
amarok(2795)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(2795)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
role  0  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QString, "Playlist Files on Disk") ,  QVariant(QString, "Internal Database") )  ) 
role  1  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QIcon, ) ,  QVariant(QIcon, ) )  ) 
role  3  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QString, "Playlist Files on Disk") ,  QVariant(QString, "Internal Database") )  ) 
QMap((0, QMap((0, QVariant(QString, "Playlist Files on Disk") ) ( 1 ,  QVariant(QIcon, ) ) ( 3 ,  QVariant(QString, "Playlist Files on Disk") ) )  ) )  
Creating empty group:  "Playlist Files on Disk" 
QMap((0, QMap((0, QVariant(QString, "Internal Database") ) ( 1 ,  QVariant(QIcon, ) ) ( 3 ,  QVariant(QString, "Internal Database") ) )  ) )  
Creating empty group:  "Internal Database" 
QMap() 
amarok(2795)/kdeui (Wallet): The kwalletd service has been disabled 
amarok(2795)/kdeui (Wallet): The kwalletd service has been disabled 
amarok(2795)/kdeui (Wallet): The kwalletd service has been disabled 
amarok(2795)/kdeui (Wallet): The kwalletd service has been disabled 
amarok(2795)/kdeui (Wallet): The kwalletd service has been disabled 
amarok(2795)/kdeui (Wallet): The kwalletd service has been disabled 
role  0  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QString, "Local Podcasts") )  ) 
role  1  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QIcon, ) )  ) 
role  3  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QString, "Local Podcasts") )  ) 
QMap((0, QMap((0, QVariant(QString, "Local Podcasts") ) ( 1 ,  QVariant(QIcon, ) ) ( 3 ,  QVariant(QString, "Local Podcasts") ) )  ) )  
Creating empty group:  "Local Podcasts" 
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x4600024
amarok:  ************************************************************************************************************ 
amarok:  ** DEBUGGING OUTPUT IS NOW ENABLED. PLEASE NOTE THAT YOU WILL ONLY SEE THE FULL OUTPUT ON THE NEXT START. ** 
amarok:  ************************************************************************************************************ 
amarok: END__: static void App::handleCliArgs() - Took 0.00016s 
amarok: END__: virtual int App::newInstance() - Took 0.00022s 
amarok: BEGIN: void CurrentEngine::stoppedState() 
amarok:    [ERROR!] Tried to perform escape() on uninitialized MySQL 
amarok: END__: void CurrentEngine::stoppedState() - Took 0.00027s 
amarok:  [ERROR!] Tried to perform query on uninitialized MySQL 
amarok: BEGIN: void CurrentTrack::dataUpdated(const QString&, const QHash<QString, QVariant>&) 
amarok: END__: void CurrentTrack::dataUpdated(const QString&, const QHash<QString, QVariant>&) - Took 0.00054s 
amarok: BEGIN: void CurrentEngine::resultReady(const QString&, const Meta::TrackList&) 
amarok: END__: void CurrentEngine::resultReady(const QString&, const Meta::TrackList&) - Took 5.8e-05s 
amarok: BEGIN: void CurrentEngine::setupTracksData() 
amarok: END__: void CurrentEngine::setupTracksData() - Took 6.4e-05s 
amarok(2795)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
antonio@antonio-portatil:~$ amarok(2795)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/antonio/.local/share/mime/magic"
QVariantMap DBusMenuExporterDBus::GetProperties(int, const QStringList&): Condition failed: action 
amarok: BEGIN: void CurrentTrack::dataUpdated(const QString&, const QHash<QString, QVariant>&) 
amarok: END__: void CurrentTrack::dataUpdated(const QString&, const QHash<QString, QVariant>&) - Took 0.00023s 
amarok: BEGIN: void ScriptUpdater::phase2(KJob*) 
amarok:   BEGIN: void ScriptManager::updaterFinished(QString) 
amarok:     BEGIN: bool ScriptManager::loadScript(const QString&) 
amarok:       [ScriptManager] script info: "Amarok Script Console"   "1.0"   "Generic"   "Amarok2.0" 
amarok:     END__: bool ScriptManager::loadScript(const QString&) - Took 0.00076s 
amarok:   END__: void ScriptManager::updaterFinished(QString) - Took 0.00095s 
amarok: END__: void ScriptUpdater::phase2(KJob*) - Took 0.0015s 
amarok: BEGIN: void ScriptUpdater::phase2(KJob*) 
amarok:   BEGIN: void ScriptManager::updaterFinished(QString) 
amarok:     BEGIN: bool ScriptManager::loadScript(const QString&) 
amarok:       [ScriptManager] script info: "Librivox.org"   "1.0"   "Scriptable Service"   "Amarok2.0" 
amarok:     END__: bool ScriptManager::loadScript(const QString&) - Took 0.00063s 
amarok:   END__: void ScriptManager::updaterFinished(QString) - Took 0.00073s 
amarok: END__: void ScriptUpdater::phase2(KJob*) - Took 0.0012s 
amarok: BEGIN: void ScriptUpdater::phase2(KJob*) 
amarok:   BEGIN: void ScriptManager::updaterFinished(QString) 
amarok:     BEGIN: bool ScriptManager::loadScript(const QString&) 
amarok:       [ScriptManager] script info: "Cool Streams"   "1.0"   "Scriptable Service"   "Amarok2.0" 
amarok:     END__: bool ScriptManager::loadScript(const QString&) - Took 0.00057s 
amarok:   END__: void ScriptManager::updaterFinished(QString) - Took 0.00068s 
amarok: END__: void ScriptUpdater::phase2(KJob*) - Took 0.00084s 
amarok: BEGIN: void ScriptUpdater::phase2(KJob*) 
amarok:   BEGIN: void ScriptManager::updaterFinished(QString) 
amarok:     BEGIN: bool ScriptManager::loadScript(const QString&) 
amarok:       [ScriptManager] script info: "Lyricwiki"   ".2"   "Lyrics"   "Amarok2.0" 
amarok:     END__: bool ScriptManager::loadScript(const QString&) - Took 0.00048s 
amarok:     BEGIN: void ScriptManager::findScripts() 
amarok:       BEGIN: void ScriptSelector::addScripts(const QList<KPluginInfo>&, KPluginSelector::PluginLoadMethod, const QString&, const QString&, const KSharedPtr<KSharedConfig>&) 
amarok(2795)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Amarok Script Console"
amarok:       END__: void ScriptSelector::addScripts(const QList<KPluginInfo>&, KPluginSelector::PluginLoadMethod, const QString&, const QString&, const KSharedPtr<KSharedConfig>&) - Took 0.004s 
amarok:       BEGIN: void ScriptSelector::addScripts(const QList<KPluginInfo>&, KPluginSelector::PluginLoadMethod, const QString&, const QString&, const KSharedPtr<KSharedConfig>&) 
amarok(2795)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "LyricWiki"
amarok:       END__: void ScriptSelector::addScripts(const QList<KPluginInfo>&, KPluginSelector::PluginLoadMethod, const QString&, const QString&, const KSharedPtr<KSharedConfig>&) - Took 0.0022s 
amarok:       BEGIN: void ScriptSelector::addScripts(const QList<KPluginInfo>&, KPluginSelector::PluginLoadMethod, const QString&, const QString&, const KSharedPtr<KSharedConfig>&) 
amarok(2795)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Cool Streams"
amarok(2795)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Librivox.org"
amarok:       END__: void ScriptSelector::addScripts(const QList<KPluginInfo>&, KPluginSelector::PluginLoadMethod, const QString&, const QString&, const KSharedPtr<KSharedConfig>&) - Took 0.0071s 
amarok:       BEGIN: void ScriptManager::slotConfigChanged(bool) 
amarok:         BEGIN: void ScriptManager::slotConfigChanged(bool) 
amarok:         END__: void ScriptManager::slotConfigChanged(bool) - Took 0.00022s 
amarok:         BEGIN: bool ScriptManager::slotRunScript(QString, bool) 
amarok:           BEGIN: void ScriptManager::startScriptEngine(QString) 
amarok:             BEGIN: ScriptableServiceScript::ScriptableServiceScript(QScriptEngine*) 
amarok:             END__: ScriptableServiceScript::ScriptableServiceScript(QScriptEngine*) - Took 0.00014s 
amarok:             BEGIN: Downloader::Downloader(QScriptEngine*) 
amarok:             END__: Downloader::Downloader(QScriptEngine*) - Took 9.8e-05s 
amarok:           END__: void ScriptManager::startScriptEngine(QString) - Took 0.002s 
amarok:           BEGIN: static QScriptValue ScriptableServiceScript::ScriptableServiceScript_prototype_ctor(QScriptContext*, QScriptEngine*) 
amarok:             BEGIN: bool ScriptableServiceManager::initService(const QString&, int, const QString&, const QString&, bool) 
amarok:                initializing scripted service:  "Cool Streams" 
amarok:               BEGIN: ServiceBase::ServiceBase(const QString&, ServiceFactory*, bool, const QString&) 
amarok:               END__: ServiceBase::ServiceBase(const QString&, ServiceFactory*, bool, const QString&) - Took 0.0061s 
amarok:               BEGIN: ScriptableService::ScriptableService(const QString&) 
amarok:                  creating ScriptableService  "Cool Streams" 
amarok:               END__: ScriptableService::ScriptableService(const QString&) - Took 0.00011s 
amarok:               BEGIN: void ScriptableService::init(int, const QString&, bool) 
amarok:                 BEGIN: ScriptableServiceCollection::ScriptableServiceCollection(const QString&) 
amarok:                 END__: ScriptableServiceCollection::ScriptableServiceCollection(const QString&) - Took 6.4e-05s 
amarok:               END__: void ScriptableService::init(int, const QString&, bool) - Took 0.00025s 
amarok:                emitting scripted service  "Cool Streams" 
amarok:               BEGIN: void ServiceBrowser::addService(ServiceBase*) 
amarok:               END__: void ServiceBrowser::addService(ServiceBase*) - Took 0.00011s 
amarok:             END__: bool ScriptableServiceManager::initService(const QString&, int, const QString&, const QString&, bool) - Took 0.0071s 
amarok:           END__: static QScriptValue ScriptableServiceScript::ScriptableServiceScript_prototype_ctor(QScriptContext*, QScriptEngine*) - Took 0.0074s 
amarok:           BEGIN: void ScriptableServiceScript::slotCustomize(const QString&) 
amarok:           END__: void ScriptableServiceScript::slotCustomize(const QString&) - Took 6.8e-05s 
amarok:         END__: bool ScriptManager::slotRunScript(QString, bool) - Took 0.063s 
amarok:         BEGIN: bool ScriptManager::slotRunScript(QString, bool) 
amarok:           BEGIN: void ScriptManager::startScriptEngine(QString) 
amarok:             BEGIN: ScriptableServiceScript::ScriptableServiceScript(QScriptEngine*) 
amarok:             END__: ScriptableServiceScript::ScriptableServiceScript(QScriptEngine*) - Took 9.2e-05s 
amarok:             BEGIN: Downloader::Downloader(QScriptEngine*) 
amarok:             END__: Downloader::Downloader(QScriptEngine*) - Took 9e-05s 
amarok:           END__: void ScriptManager::startScriptEngine(QString) - Took 0.0012s 
amarok:           BEGIN: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) 
amarok:              importing qt bindings  "qt.core" 
amarok:           END__: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) - Took 0.25s 
amarok:           BEGIN: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) 
amarok:              importing qt bindings  "qt.xml" 
amarok:           END__: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) - Took 0.34s 
amarok:           BEGIN: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) 
amarok:              importing qt bindings  "qt.network" 
amarok:           END__: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) - Took 0.012s 
amarok:           BEGIN: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) 
amarok:              importing qt bindings  "qt.gui" 
amarok:           END__: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) - Took 0.25s 
amarok:            SCRIPT "Librivox.org" :  "creating service..." 
amarok:           BEGIN: static QScriptValue ScriptableServiceScript::ScriptableServiceScript_prototype_ctor(QScriptContext*, QScriptEngine*) 
amarok:             BEGIN: bool ScriptableServiceManager::initService(const QString&, int, const QString&, const QString&, bool) 
amarok:                initializing scripted service:  "Librivox.org" 
amarok:               BEGIN: ServiceBase::ServiceBase(const QString&, ServiceFactory*, bool, const QString&) 
amarok:               END__: ServiceBase::ServiceBase(const QString&, ServiceFactory*, bool, const QString&) - Took 0.0064s 
amarok:               BEGIN: ScriptableService::ScriptableService(const QString&) 
amarok:                  creating ScriptableService  "Librivox.org" 
amarok:               END__: ScriptableService::ScriptableService(const QString&) - Took 0.0003s 
amarok:               BEGIN: void ScriptableService::init(int, const QString&, bool) 
amarok:                 BEGIN: ScriptableServiceCollection::ScriptableServiceCollection(const QString&) 
amarok:                 END__: ScriptableServiceCollection::ScriptableServiceCollection(const QString&) - Took 6.2e-05s 
amarok:               END__: void ScriptableService::init(int, const QString&, bool) - Took 0.00021s 
amarok:                emitting scripted service  "Librivox.org" 
amarok:               BEGIN: void ServiceBrowser::addService(ServiceBase*) 
amarok:               END__: void ServiceBrowser::addService(ServiceBase*) - Took 0.00011s 
amarok:             END__: bool ScriptableServiceManager::initService(const QString&, int, const QString&, const QString&, bool) - Took 0.0075s 
amarok:           END__: static QScriptValue ScriptableServiceScript::ScriptableServiceScript_prototype_ctor(QScriptContext*, QScriptEngine*) - Took 0.0076s 
amarok:            SCRIPT "Librivox.org" :  "done creating service!" 
amarok:           BEGIN: void ScriptableServiceScript::slotCustomize(const QString&) 
amarok:              SCRIPT "Librivox.org" :  "customizing Librivox service" 
amarok:              SCRIPT "Librivox.org" :  "loading icon: /usr/share/kde4/apps/amarok/scripts/librivox_service/LibrivoxIcon.png" 
amarok:             BEGIN: void ScriptableServiceManager::setIcon(const QString&, const QPixmap&) 
amarok:                service:  "Librivox.org" 
amarok:             END__: void ScriptableServiceManager::setIcon(const QString&, const QPixmap&) - Took 0.00015s 
amarok:           END__: void ScriptableServiceScript::slotCustomize(const QString&) - Took 0.018s 
amarok:         END__: bool ScriptManager::slotRunScript(QString, bool) - Took 0.91s 
amarok:         BEGIN: bool ScriptManager::slotRunScript(QString, bool) 
amarok:           BEGIN: void ScriptManager::startScriptEngine(QString) 
amarok:             BEGIN: ScriptableServiceScript::ScriptableServiceScript(QScriptEngine*) 
amarok:             END__: ScriptableServiceScript::ScriptableServiceScript(QScriptEngine*) - Took 8.6e-05s 
amarok:             BEGIN: Downloader::Downloader(QScriptEngine*) 
amarok:             END__: Downloader::Downloader(QScriptEngine*) - Took 8.8e-05s 
amarok:           END__: void ScriptManager::startScriptEngine(QString) - Took 0.0013s 
amarok:           BEGIN: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) 
amarok:              importing qt bindings  "qt.core" 
amarok:           END__: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) - Took 0.02s 
amarok:           BEGIN: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) 
amarok:              importing qt bindings  "qt.xml" 
amarok:           END__: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) - Took 0.0044s 
amarok:         END__: bool ScriptManager::slotRunScript(QString, bool) - Took 0.029s 
amarok:       END__: void ScriptManager::slotConfigChanged(bool) - Took 1s 
amarok:     END__: void ScriptManager::findScripts() - Took 1s 
amarok:   END__: void ScriptManager::updaterFinished(QString) - Took 1s 
amarok: END__: void ScriptUpdater::phase2(KJob*) - Took 1s 
antonio@antonio-portatil:~$ ^C
antonio@antonio-portatil:~$ amarok: BEGIN: void ScanManager::startIncrementalScan(const QString&) 
amarok:   BEGIN: void ScanManager::checkTables(bool) 
amarok:   END__: void ScanManager::checkTables(bool) - Took 9.4e-05s 
amarok:   BEGIN: QStringList ScanManager::getDirsToScan() 
amarok:      [ERROR!] Tried to perform query on uninitialized MySQL 
amarok:   END__: QStringList ScanManager::getDirsToScan() - Took 0.00013s 
amarok:    GOING TO SCAN: 
amarok:   BEGIN: void ScanManager::writeBatchIncrementalInfoFile() 
amarok:   END__: void ScanManager::writeBatchIncrementalInfoFile() - Took 0.00029s 
amarok:    Scanning nothing, return. 
amarok: END__: void ScanManager::startIncrementalScan(const QString&) - Took 0.00097s 
QVariantMap DBusMenuExporterDBus::GetProperties(int, const QStringList&): Condition failed: action 
amarok: BEGIN: virtual App::~App() 
amarok:   BEGIN: virtual void SqlCollection::stopScan() 
amarok:      Scan error:  "Abort requested from SqlCollection::stopScan()" 
Object::disconnect: Unexpected null parameter
Object::disconnect: Unexpected null parameter
Object::disconnect: Unexpected null parameter
QCoreApplication::postEvent: Unexpected null receiver
amarok:     BEGIN: void ScanManager::stopParser() 
amarok:     END__: void ScanManager::stopParser() - Took 5.6e-05s 
amarok:   END__: virtual void SqlCollection::stopScan() - Took 0.00026s 
amarok(2795)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok:   BEGIN: virtual ScriptManager::~ScriptManager() 
amarok:     BEGIN: void ScriptManager::slotStopScript(QString) 
amarok:       BEGIN: virtual CollectionTreeView::~CollectionTreeView() 
amarok:       END__: virtual CollectionTreeView::~CollectionTreeView() - Took 8.3e-05s 
amarok:       BEGIN: void ScriptManager::scriptFinished(QString) 
amarok:         BEGIN: virtual ScriptableServiceScript::~ScriptableServiceScript() 
amarok:         END__: virtual ScriptableServiceScript::~ScriptableServiceScript() - Took 6e-05s 
amarok:       END__: void ScriptManager::scriptFinished(QString) - Took 0.0012s 
amarok:     END__: void ScriptManager::slotStopScript(QString) - Took 0.0024s 
amarok:     BEGIN: void ScriptManager::slotStopScript(QString) 
amarok:       BEGIN: virtual CollectionTreeView::~CollectionTreeView() 
amarok:       END__: virtual CollectionTreeView::~CollectionTreeView() - Took 7.9e-05s 
amarok:       BEGIN: void ScriptManager::scriptFinished(QString) 
amarok:         BEGIN: virtual ScriptableServiceScript::~ScriptableServiceScript() 
amarok:         END__: virtual ScriptableServiceScript::~ScriptableServiceScript() - Took 6e-05s 
amarok:       END__: void ScriptManager::scriptFinished(QString) - Took 0.013s 
amarok:     END__: void ScriptManager::slotStopScript(QString) - Took 0.015s 
amarok:     BEGIN: void ScriptManager::slotStopScript(QString) 
amarok:       BEGIN: void ScriptManager::scriptFinished(QString) 
amarok:         BEGIN: virtual ScriptableServiceScript::~ScriptableServiceScript() 
amarok:         END__: virtual ScriptableServiceScript::~ScriptableServiceScript() - Took 3.4e-05s 
amarok:       END__: void ScriptManager::scriptFinished(QString) - Took 0.0033s 
amarok:     END__: void ScriptManager::slotStopScript(QString) - Took 0.0034s 
amarok:   END__: virtual ScriptManager::~ScriptManager() - Took 0.024s 
amarok:   BEGIN: virtual OSDWidget::~OSDWidget() 
amarok:   END__: virtual OSDWidget::~OSDWidget() - Took 0.00011s 
amarok:   BEGIN: virtual Amarok::KNotificationBackend::~KNotificationBackend() 
amarok:   END__: virtual Amarok::KNotificationBackend::~KNotificationBackend() - Took 4.5e-05s 
amarok(2795)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok:   BEGIN: virtual MainWindow::~MainWindow() 
amarok:     BEGIN: QString BrowserCategoryList::path() 
amarok:        path:  "root list" 
amarok:     END__: QString BrowserCategoryList::path() - Took 6.4e-05s 
amarok:     BEGIN: void MainWindow::saveLayout() 
amarok:     END__: void MainWindow::saveLayout() - Took 0.08s 
amarok:     BEGIN: virtual Context::ContextView::~ContextView() 
amarok:        Unloading plasma engine:  "amarok-photos" 
amarok:        Unloading plasma engine:  "amarok-wikipedia" 
amarok:       BEGIN: virtual WikipediaEngine::~WikipediaEngine() 
amarok:       END__: virtual WikipediaEngine::~WikipediaEngine() - Took 5.9e-05s 
amarok:       BEGIN: virtual ContextObserver::~ContextObserver() 
amarok:         BEGIN: void ContextSubject::detach(ContextObserver*) 
amarok:         END__: void ContextSubject::detach(ContextObserver*) - Took 3.3e-05s 
amarok:       END__: virtual ContextObserver::~ContextObserver() - Took 9.1e-05s 
amarok:        Unloading plasma engine:  "amarok-current" 
amarok:       BEGIN: virtual CurrentEngine::~CurrentEngine() 
amarok:       END__: virtual CurrentEngine::~CurrentEngine() - Took 4.6e-05s 
amarok:       BEGIN: virtual ContextObserver::~ContextObserver() 
amarok:         BEGIN: void ContextSubject::detach(ContextObserver*) 
amarok:         END__: void ContextSubject::detach(ContextObserver*) - Took 3.1e-05s 
amarok:       END__: virtual ContextObserver::~ContextObserver() - Took 8.6e-05s 
amarok:        Unloading plasma engine:  "amarok-videoclip" 
amarok:       BEGIN: virtual VideoclipEngine::~VideoclipEngine() 
amarok:       END__: virtual VideoclipEngine::~VideoclipEngine() - Took 4.9e-05s 
amarok:       BEGIN: virtual ContextObserver::~ContextObserver() 
amarok:         BEGIN: void ContextSubject::detach(ContextObserver*) 
amarok:         END__: void ContextSubject::detach(ContextObserver*) - Took 3e-05s 
amarok:       END__: virtual ContextObserver::~ContextObserver() - Took 9.1e-05s 
amarok:        Unloading plasma engine:  "amarok-lyrics" 
amarok:       BEGIN: virtual ContextObserver::~ContextObserver() 
amarok:         BEGIN: void ContextSubject::detach(ContextObserver*) 
amarok:         END__: void ContextSubject::detach(ContextObserver*) - Took 2.9e-05s 
amarok:       END__: virtual ContextObserver::~ContextObserver() - Took 8.4e-05s 
amarok:        Unloading plasma engine:  "amarok-info" 
amarok:       BEGIN: void Context::ContextView::clear(const Context::ContextState&) 
amarok:         BEGIN: virtual void Context::VerticalAppletLayout::saveToConfig(KConfigGroup&) 
amarok:            saving applet "Current Track" 
amarok:            saving applet "Lyrics" 
amarok:            saving applet "Wikipedia" 
amarok:            saving applet "Videoclip" 
amarok:         END__: virtual void Context::VerticalAppletLayout::saveToConfig(KConfigGroup&) - Took 0.00017s 
amarok:       END__: void Context::ContextView::clear(const Context::ContextState&) - Took 0.0045s 
amarok:     END__: virtual Context::ContextView::~ContextView() - Took 0.006s 
amarok:     BEGIN: virtual ContextSubject::~ContextSubject() 
amarok:     END__: virtual ContextSubject::~ContextSubject() - Took 3.2e-05s 
amarok:     BEGIN: virtual Context::ContextScene::~ContextScene() 
amarok:     END__: virtual Context::ContextScene::~ContextScene() - Took 0.00015s 
amarok:     BEGIN: virtual Context::Containment::~Containment() 
amarok:     END__: virtual Context::Containment::~Containment() - Took 6e-05s 
amarok:     BEGIN: virtual Context::VerticalAppletLayout::~VerticalAppletLayout() 
amarok:       BEGIN: virtual VideoclipApplet::~VideoclipApplet() 
amarok:       END__: virtual VideoclipApplet::~VideoclipApplet() - Took 0.00012s 
amarok:     END__: virtual Context::VerticalAppletLayout::~VerticalAppletLayout() - Took 0.038s 
amarok:     BEGIN: virtual StatusBar::~StatusBar() 
amarok:       BEGIN: virtual PopupWidget::~PopupWidget() 
amarok:       END__: virtual PopupWidget::~PopupWidget() - Took 3.6e-05s 
amarok:     END__: virtual StatusBar::~StatusBar() - Took 0.00037s 
amarok:     BEGIN: virtual SvgHandler::~SvgHandler() 
amarok:     END__: virtual SvgHandler::~SvgHandler() - Took 0.0033s 
amarok:     BEGIN: virtual PaletteHandler::~PaletteHandler() 
amarok:     END__: virtual PaletteHandler::~PaletteHandler() - Took 3.6e-05s 
amarok:   END__: virtual MainWindow::~MainWindow() - Took 0.14s 
amarok:   BEGIN: virtual BrowserCategoryList::~BrowserCategoryList() 
amarok:     BEGIN: virtual CollectionTreeView::~CollectionTreeView() 
amarok:     END__: virtual CollectionTreeView::~CollectionTreeView() - Took 0.0001s 
amarok:     BEGIN: virtual CollectionTreeView::~CollectionTreeView() 
amarok:       BEGIN: virtual CollectionTreeItemModel::~CollectionTreeItemModel() 
amarok:       END__: virtual CollectionTreeItemModel::~CollectionTreeItemModel() - Took 0.00012s 
amarok:     END__: virtual CollectionTreeView::~CollectionTreeView() - Took 0.00025s 
amarok:     BEGIN: void FileBrowser::writeConfig() 
amarok:     END__: void FileBrowser::writeConfig() - Took 0.05s 
amarok:     BEGIN: virtual ServiceBrowser::~ServiceBrowser() 
amarok:     END__: virtual ServiceBrowser::~ServiceBrowser() - Took 7.8e-05s 
amarok:     BEGIN: virtual BrowserCategoryList::~BrowserCategoryList() 
amarok:       BEGIN: virtual LastFmService::~LastFmService() 
amarok:       END__: virtual LastFmService::~LastFmService() - Took 6e-05s 
amarok:       BEGIN: virtual CollectionTreeView::~CollectionTreeView() 
amarok:       END__: virtual CollectionTreeView::~CollectionTreeView() - Took 3.9e-05s 
amarok:     END__: virtual BrowserCategoryList::~BrowserCategoryList() - Took 0.00096s 
amarok:     BEGIN: virtual ScriptableServiceManager::~ScriptableServiceManager() 
amarok:     END__: virtual ScriptableServiceManager::~ScriptableServiceManager() - Took 3.8e-05s 
amarok:     BEGIN: virtual BrowserCategoryList::~BrowserCategoryList() 
amarok:       BEGIN: void PlaylistBrowserNS::DynamicCategory::saveOnExit() 
amarok:         BEGIN: void PlaylistBrowserNS::DynamicModel::saveCurrent() 
amarok:         END__: void PlaylistBrowserNS::DynamicModel::saveCurrent() - Took 0.00045s 
amarok:       END__: void PlaylistBrowserNS::DynamicCategory::saveOnExit() - Took 0.00052s 
amarok:     END__: virtual BrowserCategoryList::~BrowserCategoryList() - Took 0.0018s 
amarok:   END__: virtual BrowserCategoryList::~BrowserCategoryList() - Took 0.059s 
amarok:   BEGIN: virtual BrowserBreadcrumbItem::~BrowserBreadcrumbItem() 
amarok:   END__: virtual BrowserBreadcrumbItem::~BrowserBreadcrumbItem() - Took 3.5e-05s 
amarok:   BEGIN: virtual CollectionManager::~CollectionManager() 
amarok:     BEGIN: virtual MySqlEmbeddedStorage::~MySqlEmbeddedStorage() 
amarok:     END__: virtual MySqlEmbeddedStorage::~MySqlEmbeddedStorage() - Took 4.4e-05s 
amarok:     BEGIN: virtual MySqlStorage::~MySqlStorage() 
amarok:     END__: virtual MySqlStorage::~MySqlStorage() - Took 3.4e-05s 
amarok:     BEGIN: virtual MountPointManager::~MountPointManager() 
amarok:     END__: virtual MountPointManager::~MountPointManager() - Took 4.8e-05s 
amarok:     BEGIN: virtual ScanManager::~ScanManager() 
amarok:       BEGIN: void ScanManager::stopParser() 
amarok:       END__: void ScanManager::stopParser() - Took 3.2e-05s 
amarok:     END__: virtual ScanManager::~ScanManager() - Took 9.2e-05s 
amarok:     BEGIN: virtual MtpCollectionFactory::~MtpCollectionFactory() 
amarok:     END__: virtual MtpCollectionFactory::~MtpCollectionFactory() - Took 8.2e-05s 
amarok:   END__: virtual CollectionManager::~CollectionManager() - Took 0.0021s 
amarok:   BEGIN: virtual Playlist::Actions::~Actions() 
amarok:   END__: virtual Playlist::Actions::~Actions() - Took 3.8e-05s 
amarok:   BEGIN: virtual Playlist::Model::~Model() 
amarok:     BEGIN: Meta::XSPFPlaylist::XSPFPlaylist(Meta::TrackList) 
amarok:       BEGIN: virtual void Meta::XSPFPlaylist::setTrackList(Meta::TrackList, bool) 
amarok:       END__: virtual void Meta::XSPFPlaylist::setTrackList(Meta::TrackList, bool) - Took 0.00041s 
amarok:     END__: Meta::XSPFPlaylist::XSPFPlaylist(Meta::TrackList) - Took 0.0005s 
amarok:     BEGIN: virtual bool Meta::XSPFPlaylist::save(const KUrl&, bool) 
amarok:        Saving to  KUrl("file:///home/antonio/.kde/share/apps/amarok/current.xspf") 
amarok:     END__: virtual bool Meta::XSPFPlaylist::save(const KUrl&, bool) - Took 0.0017s 
amarok:   END__: virtual Playlist::Model::~Model() - Took 0.0026s 
amarok:   BEGIN: virtual PlaylistFileProvider::~PlaylistFileProvider() 
amarok:      0  Playlists loaded 
amarok:   END__: virtual PlaylistFileProvider::~PlaylistFileProvider() - Took 0.00012s 
amarok:   BEGIN: virtual EngineController::~EngineController() 
amarok:   END__: virtual EngineController::~EngineController() - Took 0.0025s 
amarok: END__: virtual App::~App() - Took 0.28s 
amarok: BEGIN: virtual Dynamic::BiasedPlaylist::~BiasedPlaylist() 
amarok: END__: virtual Dynamic::BiasedPlaylist::~BiasedPlaylist() - Took 7.5e-05s 
^C
antonio@antonio-portatil:~$
```

---

### Post by kukker32 on 2010-07-16
when you are about to close it... try terminate it instead..

hit alt+F2 type in xkill

and then with the cross press on amarok window

---

### Post by alt126 on 2010-07-16
But...this is to close Amarok process...but i would like to get something to fix this...

Thanks

---

### Post by MadCatmkII on 2010-07-19
I have the very same problem in 10.04. The amarok process refuses to die willingly when I do ctrl-q or just chooses quit in the menu.

For some strange reason it also crashes completely if I choose to rescan my musik collection. Does that happen to you?

---

