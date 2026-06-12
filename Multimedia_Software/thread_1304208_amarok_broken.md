---
title: "amarok broken"
date: 2009-10-29
forum: Multimedia Software
---

### Post by sphilli8 on 2009-10-29
Until recently, I had no problems playing mp3 files in Amarok and JuK. I don't know what caused it, but now I can't play them. Codecs are installed. Sound works fine for skype, firefox etc. Guess that means it's a xine problem?


When I run JuK from terminal, the following error message shows:
```
xine is asking to seek behind the end of the data stream
```

when I run "amarok --debug" from terminal, here's what comes up:

```
$ amarok --debug
Object::connect: No such signal KLineEdit::downPressed() in /build/buildd/amarok-2.1.1mysql5.1.30/amarok-2.1.1/src/widgets/ProgressiveSearchWidget.cpp:57
amarok:  ************************************************************************************************************                                    
amarok:  ** DEBUGGING OUTPUT IS NOW ENABLED. PLEASE NOTE THAT YOU WILL ONLY SEE THE FULL OUTPUT ON THE NEXT START. **                                    
amarok:  ************************************************************************************************************                                    
amarok: END__: static void App::handleCliArgs() - Took 0.00045s                                                                                          
amarok: END__: virtual int App::newInstance() - Took 0.00062s                                                                                            
sphilli8@sphilli8-laptop:~$ amarok: [MountPointManager] [WARNING!] NOT-IMPLEMENTED:  void MountPointManager::startStatisticsUpdateJob()                  

amarok: BEGIN: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) 
amarok:    importing qt bindings  "qt.xml"                                      
amarok: END__: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) - Took 0.59s 
amarok: BEGIN: void CurrentEngine::stoppedState()                                            
amarok: END__: void CurrentEngine::stoppedState() - Took 0.00094s                            
amarok:  Initialized thread, count== 2                                                       
amarok: BEGIN: void Albums::dataUpdated(const QString&, const QHash<QString, QVariant>&)     
amarok: END__: void Albums::dataUpdated(const QString&, const QHash<QString, QVariant>&) - Took 0.00016s 
amarok:  [ERROR!] Tried to perform query on uninitialized MySQLe                                         
amarok: BEGIN: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&)                          
amarok:    importing qt bindings  "qt.network"                                                           
amarok: END__: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) - Took 0.056s            
amarok: BEGIN: void Albums::dataUpdated(const QString&, const QHash<QString, QVariant>&)                 
amarok: END__: void Albums::dataUpdated(const QString&, const QHash<QString, QVariant>&) - Took 0.00015s 
amarok: BEGIN: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&)                          
amarok:    importing qt bindings  "qt.gui"                                                               
amarok: END__: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) - Took 0.36s             
amarok:  SCRIPT "Librivox.org" :  "creating service..."                                                  
amarok: BEGIN: static QScriptValue ScriptableServiceScript::ScriptableServiceScript_prototype_ctor(QScriptContext*, QScriptEngine*) 
amarok:   BEGIN: bool ScriptableServiceManager::initService(const QString&, int, const QString&, const QString&, bool)              
amarok:      initializing scripted service:  "Librivox.org"                                                                         
amarok:     BEGIN: ServiceBase::ServiceBase(const QString&, ServiceFactory*, bool, const QString&)                                  
amarok:     END__: ServiceBase::ServiceBase(const QString&, ServiceFactory*, bool, const QString&) - Took 0.0024s                   
amarok:     BEGIN: void ServiceBase::setIcon(const QIcon&)                                                                          
amarok:     END__: void ServiceBase::setIcon(const QIcon&) - Took 0.00011s                                                          
amarok:     BEGIN: void ScriptableService::init(int, const QString&, bool)                                                          
amarok:       BEGIN: ScriptableServiceCollection::ScriptableServiceCollection(const QString&)                                       
amarok:       END__: ScriptableServiceCollection::ScriptableServiceCollection(const QString&) - Took 0.00012s                       
amarok:     END__: void ScriptableService::init(int, const QString&, bool) - Took 0.00036s                                          
amarok:   END__: bool ScriptableServiceManager::initService(const QString&, int, const QString&, const QString&, bool) - Took 0.0035s 
amarok: END__: static QScriptValue ScriptableServiceScript::ScriptableServiceScript_prototype_ctor(QScriptContext*, QScriptEngine*) - Took 0.0038s 
amarok:  SCRIPT "Librivox.org" :  "done creating service!"                                                                                         
amarok: BEGIN: void ScriptableServiceScript::slotCustomize(const QString&)                                                                         
amarok:    SCRIPT "Librivox.org" :  "customizing Librivox service"                                                                                 
amarok:    SCRIPT "Librivox.org" :  "loading icon: /usr/share/kde4/apps/amarok/scripts/librivox_service/LibrivoxIcon.png"                          
amarok:   BEGIN: void ScriptableServiceManager::setIcon(const QString&, const QPixmap&)                                                            
amarok:      service:  "Librivox.org"                                                                                                              
amarok:     BEGIN: void ServiceBase::setIcon(const QIcon&)                                                                                         
amarok:     END__: void ServiceBase::setIcon(const QIcon&) - Took 9.4e-05s                                                                         
amarok:   END__: void ScriptableServiceManager::setIcon(const QString&, const QPixmap&) - Took 0.0003s                                             
amarok: END__: void ScriptableServiceScript::slotCustomize(const QString&) - Took 0.029s                                                           
amarok: END__: bool ScriptManager::slotRunScript(QString, bool) - Took 1.5s                                                                        
amarok: BEGIN: bool ScriptManager::slotRunScript(QString, bool)                                                                                    
amarok:   BEGIN: void ScriptManager::startScriptEngine(QString)                                                                                    
amarok:     BEGIN: ScriptableServiceScript::ScriptableServiceScript(QScriptEngine*)                                                                
amarok:     END__: ScriptableServiceScript::ScriptableServiceScript(QScriptEngine*) - Took 7.7e-05s                                                
amarok:     BEGIN: Downloader::Downloader(QScriptEngine*)                                                                                          
amarok:     END__: Downloader::Downloader(QScriptEngine*) - Took 9.6e-05s                                                                          
amarok:   END__: void ScriptManager::startScriptEngine(QString) - Took 0.0011s                                                                     
amarok:   BEGIN: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&)                                                                  
amarok:      importing qt bindings  "qt.core"                                                                                                      
amarok:   END__: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) - Took 0.023s                                                    
amarok:   BEGIN: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&)                                                                  
amarok:      importing qt bindings  "qt.xml"                                                                                                       
amarok:   END__: bool AmarokScript::ScriptImporter::loadQtBinding(const QString&) - Took 0.017s                                                    
amarok: END__: bool ScriptManager::slotRunScript(QString, bool) - Took 0.049s                                                                      
amarok: END__: void ScriptManager::slotConfigChanged(bool) - Took 1.6s                                                                             
amarok: END__: void ScriptManager::findScripts() - Took 1.6s                                                                                       
amarok: BEGIN: virtual void MainToolbar::resizeEvent(QResizeEvent*)                                                                                
amarok: END__: virtual void MainToolbar::resizeEvent(QResizeEvent*) - Took 0.00018s                                                                
amarok: BEGIN: void Playlist::PrettyListView::fixInvisible()                                                                                       
amarok: END__: void Playlist::PrettyListView::fixInvisible() - Took 0.00032s                                                                       
amarok: BEGIN: SvgHandler::SvgHandler(QObject*)                                                                                                    
amarok: END__: SvgHandler::SvgHandler(QObject*) - Took 0.00031s                                                                                    
amarok: BEGIN: void EngineController::playPause()                                                                                                  
amarok:   [EngineController] PlayPause: phonon state 0                                                                                             
amarok:   BEGIN: void EngineController::play()                                                                                                     
amarok:     BEGIN: void Playlist::Actions::play(quint64, bool)                                                                                     
amarok:       [Playlist::Actions] [WARNING!] Invalid trackid 0                                                                                     
amarok:     END__: void Playlist::Actions::play(quint64, bool) - Took 0.00019s                                                                     
amarok:   END__: void EngineController::play() - Took 0.00041s                                                                                     
amarok: END__: void EngineController::playPause() - Took 0.00077s                                                                                  
amarok: BEGIN: void ScanManager::startIncrementalScan()                                                                                            
amarok:   BEGIN: QStringList ScanManager::getDirsToScan()                                                                                          
amarok:      [ERROR!] Tried to perform query on uninitialized MySQLe                                                                               
amarok:   END__: QStringList ScanManager::getDirsToScan() - Took 0.00021s                                                                          
amarok:    GOING TO SCAN:                                                                                                                          
amarok:    Scanning nothing, return.                                                                                                               
amarok:   BEGIN: void ScanManager::writeBatchIncrementalInfoFile()                                                                                 
amarok:   END__: void ScanManager::writeBatchIncrementalInfoFile() - Took 0.00043s                                                                 
amarok: END__: void ScanManager::startIncrementalScan() - Took 0.0013s                                                                             
amarok: BEGIN: void EngineController::playPause()                                                                                                  
amarok:   [EngineController] PlayPause: phonon state 0                                                                                             
amarok:   BEGIN: void EngineController::play()                                                                                                     
amarok:     BEGIN: void Playlist::Actions::play(quint64, bool)                                                                                     
amarok:       [Playlist::Actions] [WARNING!] Invalid trackid 0                                                                                     
amarok:     END__: void Playlist::Actions::play(quint64, bool) - Took 0.00018s                                                                     
amarok:   END__: void EngineController::play() - Took 0.00044s                                                                                     
amarok: END__: void EngineController::playPause() - Took 0.00088s                                                                                  
amarok: BEGIN: void EngineController::playPause()                                                                                                  
amarok:   [EngineController] PlayPause: phonon state 0                                                                                             
amarok:   BEGIN: void EngineController::play()                                                                                                     
amarok:     BEGIN: void Playlist::Actions::play(quint64, bool)                                                                                     
amarok:       [Playlist::Actions] [WARNING!] Invalid trackid 0                                                                                     
amarok:     END__: void Playlist::Actions::play(quint64, bool) - Took 0.00018s                                                                     
amarok:   END__: void EngineController::play() - Took 0.00045s                                                                                     
amarok: END__: void EngineController::playPause() - Took 0.00082s                                                                                  
amarok: BEGIN: void ScanManager::startIncrementalScan()                                                                                            
amarok:   BEGIN: QStringList ScanManager::getDirsToScan()                                                                                          
amarok:      [ERROR!] Tried to perform query on uninitialized MySQLe                                                                               
amarok:   END__: QStringList ScanManager::getDirsToScan() - Took 0.00021s                                                                          
amarok:    GOING TO SCAN:                                                                                                                          
amarok:    Scanning nothing, return.                                                                                                               
amarok:   BEGIN: void ScanManager::writeBatchIncrementalInfoFile()                                                                                 
amarok:   END__: void ScanManager::writeBatchIncrementalInfoFile() - Took 0.00043s                                                                 
amarok: END__: void ScanManager::startIncrementalScan() - Took 0.0013s                                                                             
amarok: BEGIN: void ScanManager::startIncrementalScan()                                                                                            
amarok:   BEGIN: QStringList ScanManager::getDirsToScan()                                                                                          
amarok:      [ERROR!] Tried to perform query on uninitialized MySQLe                                                                               
amarok:   END__: QStringList ScanManager::getDirsToScan() - Took 0.00021s
amarok:    GOING TO SCAN:
amarok:    Scanning nothing, return.
amarok:   BEGIN: void ScanManager::writeBatchIncrementalInfoFile()
amarok:   END__: void ScanManager::writeBatchIncrementalInfoFile() - Took 0.00048s
amarok: END__: void ScanManager::startIncrementalScan() - Took 0.0013s
amarok: BEGIN: void ScanManager::startIncrementalScan()
amarok:   BEGIN: QStringList ScanManager::getDirsToScan()
amarok:      [ERROR!] Tried to perform query on uninitialized MySQLe
amarok:   END__: QStringList ScanManager::getDirsToScan() - Took 0.00021s
amarok:    GOING TO SCAN:
amarok:    Scanning nothing, return.
amarok:   BEGIN: void ScanManager::writeBatchIncrementalInfoFile()
amarok:   END__: void ScanManager::writeBatchIncrementalInfoFile() - Took 0.00045s
amarok: END__: void ScanManager::startIncrementalScan() - Took 0.0013s
amarok: BEGIN: void ScanManager::startIncrementalScan()
amarok:   BEGIN: QStringList ScanManager::getDirsToScan()
amarok:      [ERROR!] Tried to perform query on uninitialized MySQLe
amarok:   END__: QStringList ScanManager::getDirsToScan() - Took 0.00021s
amarok:    GOING TO SCAN:
amarok:    Scanning nothing, return.
amarok:   BEGIN: void ScanManager::writeBatchIncrementalInfoFile()
amarok:   END__: void ScanManager::writeBatchIncrementalInfoFile() - Took 0.00043s
amarok: END__: void ScanManager::startIncrementalScan() - Took 0.0013s

```

---

