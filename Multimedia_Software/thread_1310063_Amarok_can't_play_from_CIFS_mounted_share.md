---
title: "Amarok can't play from CIFS mounted share"
date: 2009-11-01
forum: Multimedia Software
---

### Post by pumrel on 2009-11-01
Hello guys,
I swear I looked both here and on KDE forums, but didn't find a solution.
Now, when I'm on Karmic and with Amarok 2.2 I can't play any song from my shared collection.
fstab entry follows:
```
//192.168.2.118/Volume_1	/media/ULOZISTE	cifs	guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0
```
If I try to play them, It just flicks rapidly through them stating that there were too many errors.
What's a bit strange is that Amarok shows a collection named "Shared music on Dlink-7e3030", which doesn't contain all the music though. and it's possible to play it. A path to these files begin with daap:// (I don't know what it means) :(

I tried to run amarok with -debug and the result is:
```
amarok:  Drop from external source or file browser                     
amarok:  not a track no match                                          
amarok:  [CUEFILE]:  "/media/ULOZISTE/#Hudba/EF/Give Me Beauty...Or Give Me Death!/01-ef-ett.cue"  - Shoot blindly and missed, searching for other cue files.                                                        
amarok:  [CUEFILE]: - Didn't find any matching cue file.               

amarok:  possible encoding:  "UTF-8" 
amarok:  encoding decoded as UTF-8   
amarok:  "Read metadata from file for: Ett" 
amarok: BEGIN: void Playlist::Controller::slotFinishDirectoryLoader(const Meta::TrackList&)                                                   
amarok:   BEGIN: void Playlist::Controller::insertOptioned(Meta::TrackList, int)                                                              
amarok:     [Playlist::Controller] engine state:  0                    
amarok:     BEGIN: void Playlist::Actions::play(quint64, bool)         
amarok:       BEGIN: void EngineController::play(const Meta::TrackPtr&, uint)                                                                 
amarok:         [EngineController] Just a normal, boring track... :-P  
amarok:         BEGIN: void EngineController::playUrl(const KUrl&, uint)                                                                      
amarok:           [EngineController] URL:  "file:///media/ULOZISTE/%23Hudba/EF/Give%20Me%20Beauty...Or%20Give%20Me%20Death!/01-ef-ett.mp3"    
amarok:           BEGIN: void EngineController::slotNewTrackPlaying(const Phonon::MediaSource&)                                               
amarok:             [EngineController] Using gain of 0 with relative peak of 0                                                                
amarok:             BEGIN: virtual void ProgressWidget::engineNewTrackPlaying()                                                               
amarok:               BEGIN: virtual void ProgressWidget::engineTrackLengthChanged(long int)                                                  
amarok:                  new length:  241                              
amarok:                  slider enabled!                               
amarok:                 BEGIN: void ProgressWidget::redrawBookmarks()  
amarok:                    found  0  timecodes on this track           
amarok:                 END__: void ProgressWidget::redrawBookmarks() - Took 0.00063s                                                         
amarok:               END__: virtual void ProgressWidget::engineTrackLengthChanged(long int) - Took 0.00077s                                  
amarok:             END__: virtual void ProgressWidget::engineNewTrackPlaying() - Took 0.00089s                                               
amarok:             BEGIN: void Playlist::PrettyListView::scrollToActiveTrack()                                                               
amarok:               [Playlist::PrettyListView] skipping scroll? false                                                                       
amarok:             END__: void Playlist::PrettyListView::scrollToActiveTrack() - Took 7.4e-05s                                               
amarok:             BEGIN: virtual void TimecodeObserver::engineNewTrackPlaying()                                                             
amarok:                curent track name:  "Ett"                       
amarok:                Track timecodeable                              
amarok:             END__: virtual void TimecodeObserver::engineNewTrackPlaying() - Took 9.2e-05s                                             
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.                                                     
amarok:              returning bookmarkcurrenttrack action             
amarok:             BEGIN: virtual void Context::ContextView::engineNewTrackPlaying()                                                         
amarok:               BEGIN: virtual void CurrentEngine::message(const Context::ContextState&)                                                
amarok:                 BEGIN: void CurrentEngine::update()            
amarok:                 END__: void CurrentEngine::update() - Took 0.017s                                                                     
amarok:               END__: virtual void CurrentEngine::message(const Context::ContextState&) - Took 0.017s                                  
amarok:               BEGIN: void WikipediaEngine::update()            
amarok:                 BEGIN: bool EngineController::isStream()       
amarok:                 END__: bool EngineController::isStream() - Took 4.6e-05s                                                              
amarok:                  wiki url:  "http://en.wikipedia.org/w/index.php?title=Ef%20%28band%29&useskin=monobook"                              
amarok:               END__: void WikipediaEngine::update() - Took 0.00028s                                                                   
amarok:             END__: virtual void Context::ContextView::engineNewTrackPlaying() - Took 0.017s                                           
amarok:             BEGIN: virtual void ProgressWidget::engineNewTrackPlaying()                                                               
amarok:               BEGIN: virtual void ProgressWidget::engineTrackLengthChanged(long int)                                                  
amarok:                  new length:  241                              
amarok:                  slider enabled!                               
amarok:                 BEGIN: void ProgressWidget::redrawBookmarks()  
amarok:                    found  0  timecodes on this track           
amarok:                 END__: void ProgressWidget::redrawBookmarks() - Took 0.00027s                                                         
amarok:               END__: virtual void ProgressWidget::engineTrackLengthChanged(long int) - Took 0.00037s                                  
amarok:             END__: virtual void ProgressWidget::engineNewTrackPlaying() - Took 0.00044s                                               
amarok:             BEGIN: virtual void ScrobblerAdapter::engineNewTrackPlaying()                                                             
amarok:               [lastfm] track type: "mp3"                       
amarok:               BEGIN: void ScrobblerAdapter::checkScrobble()    
amarok:                 [lastfm] total played 0 duration 0 isNull false submit? true                                                          
amarok:                 [lastfm] scrobble:  "[unknown]"  -  "[unknown]"  -  "[unknown]"                                                       
0                                                                      
amarok:               END__: void ScrobblerAdapter::checkScrobble() - Took 0.00015s                                                           
amarok:               [lastfm] nowPlaying:  "Ef"  -  "Give Me Beauty... Or Give Me Death!-(JP Import)"  -  "Ett"                              
HTTP POST:  QUrl( "http://post.audioscrobbler.com:80/np_1.2" )  "a=Ef&t=Ett&b=Give%20Me%20Beauty...%20Or%20Give%20Me%20Death%21-%28JP%20Import%29&l=241&n=0&m="                   
amarok:             END__: virtual void ScrobblerAdapter::engineNewTrackPlaying() - Took 0.00049s                                             
amarok:           END__: void EngineController::slotNewTrackPlaying(const Phonon::MediaSource&) - Took 0.04s                                  
amarok:         END__: void EngineController::playUrl(const KUrl&, uint) - Took 0.04s                                                         
amarok:       END__: void EngineController::play(const Meta::TrackPtr&, uint) - Took 0.04s                                                    
amarok:     END__: void Playlist::Actions::play(quint64, bool) - Took 0.041s                                                                  
amarok:   END__: void Playlist::Controller::insertOptioned(Meta::TrackList, int) - Took 0.042s                                                
amarok: END__: void Playlist::Controller::slotFinishDirectoryLoader(const Meta::TrackList&) - Took 0.042s                                     
amarok: BEGIN: void EngineController::slotStateChanged(Phonon::State, Phonon::State)                                                          
amarok:   [EngineController] [WARNING!] Phonon failed to play this URL. Error:  "Cannot find demultiplexer plugin for MRL [file://media/ULOZISTE/#Hudba/EF/Give Me Beauty...Or Give Me Death!/01-ef-ett.mp3]"        
amarok:   BEGIN: void Playlist::Actions::requestNextTrack()            
amarok:     [Playlist::Actions] so far so good!                        
amarok:     [Playlist::Actions] nothing more to play...                
amarok:   END__: void Playlist::Actions::requestNextTrack() - Took 0.00011s                                                                   
amarok:   BEGIN: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State)                                                         
amarok:     BEGIN: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State)                                              
amarok:     END__: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State) - Took 4.4e-05s                              
amarok:     BEGIN: virtual void SqlPodcastProvider::engineStateChanged(Phonon::State, Phonon::State)                                          
amarok:        NEWSTATE:  5 OLDSTATE:  0                               
amarok:     END__: virtual void SqlPodcastProvider::engineStateChanged(Phonon::State, Phonon::State) - Took 7e-05s                            
amarok:      returning bookmarkcurrenttrack action                     
amarok:     BEGIN: virtual void MainWindow::engineStateChanged(Phonon::State, Phonon::State)                                                  
amarok:       [MainWindow] Phonon state:  5                            
amarok:     END__: virtual void MainWindow::engineStateChanged(Phonon::State, Phonon::State) - Took 8.6e-05s                                  
amarok:     BEGIN: virtual void StatusBar::engineStateChanged(Phonon::State, Phonon::State)                                                   
amarok:     END__: virtual void StatusBar::engineStateChanged(Phonon::State, Phonon::State) - Took 4.5e-05s                                   
amarok:     [Playlist::Actions] [WARNING!] Error, can not play this track.                                                                    
amarok:     [Playlist::Actions] [WARNING!] Failure count:  1           
amarok:     BEGIN: virtual void Amarok::OSD::engineStateChanged(Phonon::State, Phonon::State)                                                 
amarok:     END__: virtual void Amarok::OSD::engineStateChanged(Phonon::State, Phonon::State) - Took 4.6e-05s                                 
amarok:     BEGIN: virtual void Amarok::PlayPauseAction::engineStateChanged(Phonon::State, Phonon::State)                                     
amarok:        NEWSTATE:  5 OLDSTATE:  0                               
amarok:     END__: virtual void Amarok::PlayPauseAction::engineStateChanged(Phonon::State, Phonon::State) - Took 7e-05s                       
amarok:      returning bookmarkcurrenttrack action                     
amarok:     BEGIN: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State)                                              
amarok:     END__: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State) - Took 4.9e-05s                              
amarok:   END__: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State) - Took 0.0081s                                          
amarok: END__: void EngineController::slotStateChanged(Phonon::State, Phonon::State) - Took 0.0084s                                           
amarok: BEGIN: void CurrentTrack::dataUpdated(const QString&, const QHash<QString, QVariant>&)                                                
amarok:    returning bookmarkcurrenttrack action                       
amarok: END__: void CurrentTrack::dataUpdated(const QString&, const QHash<QString, QVariant>&) - Took 0.0024s                                 
amarok: BEGIN: void Playlist::Controller::insertOptioned(Meta::TrackPtr, int)                                                                 
amarok:   BEGIN: void Playlist::Controller::insertOptioned(Meta::TrackList, int)                                                              
amarok:     [Playlist::Controller] engine state:  5                    
amarok:   END__: void Playlist::Controller::insertOptioned(Meta::TrackList, int) - Took 0.00039s                                              
amarok: END__: void Playlist::Controller::insertOptioned(Meta::TrackPtr, int) - Took 0.00049s                                                 
amarok: BEGIN: void ProgressWidget::redrawBookmarks()                  
amarok:    found  0  timecodes on this track                           
amarok: END__: void ProgressWidget::redrawBookmarks() - Took 0.00031s  
amarok: BEGIN: void ProgressWidget::redrawBookmarks()                  
amarok:    found  0  timecodes on this track                           
amarok: END__: void ProgressWidget::redrawBookmarks() - Took 0.00021s  
amarok: BEGIN: void WikipediaEngine::wikiResult(KJob*)                 
amarok: END__: void WikipediaEngine::wikiResult(KJob*) - Took 0.0024s  
amarok: BEGIN: virtual void TextScrollingWidget::hoverEnterEvent(QGraphicsSceneHoverEvent*)                                                   
amarok: END__: virtual void TextScrollingWidget::hoverEnterEvent(QGraphicsSceneHoverEvent*) - Took 0.00021s                                   
"OK"                                                                   
amarok: BEGIN: virtual void Playlist::PrettyListView::contextMenuEvent(QContextMenuEvent*)                                                    
amarok:   BEGIN: void Playlist::ViewCommon::trackMenu(QWidget*, const QModelIndex*, const QPoint&, bool)                                      
amarok:     BEGIN: void Playlist::Controller::removeRows(QList<int>&)  
amarok:       [Playlist::Controller] Removing row  1                   
amarok:       BEGIN: void Playlist::Model::removeTracksCommand(const Playlist::RemoveCmdList&)                                                
amarok:       END__: void Playlist::Model::removeTracksCommand(const Playlist::RemoveCmdList&) - Took 0.00055s                                
amarok:     END__: void Playlist::Controller::removeRows(QList<int>&) - Took 0.00077s                                                         
amarok:   END__: void Playlist::ViewCommon::trackMenu(QWidget*, const QModelIndex*, const QPoint&, bool) - Took 3.1s                          
amarok: END__: virtual void Playlist::PrettyListView::contextMenuEvent(QContextMenuEvent*) - Took 3.1s                                        
amarok: BEGIN: void Playlist::PrettyListView::trackActivated(const QModelIndex&)                                                              
amarok:   BEGIN: void Playlist::Actions::play(quint64, bool)           
amarok:     BEGIN: void EngineController::play(const Meta::TrackPtr&, uint)                                                                   
amarok:       [EngineController] Just a normal, boring track... :-P    
amarok:       BEGIN: void EngineController::playUrl(const KUrl&, uint) 
amarok:         [EngineController] URL:  "file:///media/ULOZISTE/%23Hudba/EF/Give%20Me%20Beauty...Or%20Give%20Me%20Death!/01-ef-ett.mp3"      
amarok:         BEGIN: void EngineController::slotNewTrackPlaying(const Phonon::MediaSource&)                                                 
amarok:           [EngineController] Using gain of 0 with relative peak of 0                                                                  
amarok:           BEGIN: virtual void ProgressWidget::engineNewTrackPlaying()                                                                 
amarok:             BEGIN: virtual void ProgressWidget::engineTrackLengthChanged(long int)                                                    
amarok:                new length:  241                                
amarok:                slider enabled!                                 
amarok:               BEGIN: void ProgressWidget::redrawBookmarks()    
amarok:                  found  0  timecodes on this track             
amarok:               END__: void ProgressWidget::redrawBookmarks() - Took 0.00036s                                                           
amarok:             END__: virtual void ProgressWidget::engineTrackLengthChanged(long int) - Took 0.00051s                                    
amarok:           END__: virtual void ProgressWidget::engineNewTrackPlaying() - Took 0.0006s                                                  
amarok:           BEGIN: void Playlist::PrettyListView::scrollToActiveTrack()                                                                 
amarok:             [Playlist::PrettyListView] skipping scroll? true   
amarok:           END__: void Playlist::PrettyListView::scrollToActiveTrack() - Took 7.2e-05s                                                 
amarok:           BEGIN: virtual void TimecodeObserver::engineNewTrackPlaying()                                                               
amarok:           END__: virtual void TimecodeObserver::engineNewTrackPlaying() - Took 4.4e-05s                                               
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.                                                     
amarok:            returning bookmarkcurrenttrack action               
amarok:           BEGIN: virtual void Context::ContextView::engineNewTrackPlaying()                                                           
amarok:             BEGIN: virtual void CurrentEngine::message(const Context::ContextState&)                                                  
amarok:               BEGIN: void CurrentEngine::update()              
amarok:               END__: void CurrentEngine::update() - Took 0.002s                                                                       
amarok:             END__: virtual void CurrentEngine::message(const Context::ContextState&) - Took 0.0021s                                   
amarok:             BEGIN: void WikipediaEngine::update()              
amarok:               BEGIN: bool EngineController::isStream()         
amarok:               END__: bool EngineController::isStream() - Took 4.8e-05s                                                                
amarok:                Same entry requested again. Ignoring.           
amarok:             END__: void WikipediaEngine::update() - Took 0.00017s                                                                     
amarok:           END__: virtual void Context::ContextView::engineNewTrackPlaying() - Took 0.0024s                                            
amarok:           BEGIN: virtual void ProgressWidget::engineNewTrackPlaying()                                                                 
amarok:             BEGIN: virtual void ProgressWidget::engineTrackLengthChanged(long int)                                                    
amarok:                new length:  241                                
amarok:                slider enabled!                                 
amarok:               BEGIN: void ProgressWidget::redrawBookmarks()    
amarok:                  found  0  timecodes on this track             
amarok:               END__: void ProgressWidget::redrawBookmarks() - Took 0.00033s                                                           
amarok:             END__: virtual void ProgressWidget::engineTrackLengthChanged(long int) - Took 0.00047s                                    
amarok:           END__: virtual void ProgressWidget::engineNewTrackPlaying() - Took 0.00056s                                                 
amarok:           BEGIN: virtual void ScrobblerAdapter::engineNewTrackPlaying()                                                               
amarok:             [lastfm] track type: "mp3"                         
amarok:             BEGIN: void ScrobblerAdapter::checkScrobble()      
amarok:               [lastfm] total played 0 duration 120500 isNull false submit? true                                                       
amarok:             END__: void ScrobblerAdapter::checkScrobble() - Took 7.6e-05s                                                             
amarok:             [lastfm] nowPlaying:  "Ef"  -  "Give Me Beauty... Or Give Me Death!-(JP Import)"  -  "Ett"                                
amarok:           END__: virtual void ScrobblerAdapter::engineNewTrackPlaying() - Took 0.00026s                                               
amarok:         END__: void EngineController::slotNewTrackPlaying(const Phonon::MediaSource&) - Took 0.013s                                   
amarok:       END__: void EngineController::playUrl(const KUrl&, uint) - Took 0.016s                                                          
amarok:     END__: void EngineController::play(const Meta::TrackPtr&, uint) - Took 0.017s                                                     
amarok:   END__: void Playlist::Actions::play(quint64, bool) - Took 0.017s                                                                    
amarok: END__: void Playlist::PrettyListView::trackActivated(const QModelIndex&) - Took 0.017s                                                
amarok: BEGIN: void EngineController::slotStateChanged(Phonon::State, Phonon::State)                                                          
amarok:   BEGIN: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State)                                                         
amarok:     BEGIN: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State)                                              
amarok:     END__: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State) - Took 4.8e-05s                              
amarok:     BEGIN: virtual void SqlPodcastProvider::engineStateChanged(Phonon::State, Phonon::State)                                          
amarok:        NEWSTATE:  0 OLDSTATE:  5                               
amarok:     END__: virtual void SqlPodcastProvider::engineStateChanged(Phonon::State, Phonon::State) - Took 6.9e-05s                          
amarok:      returning bookmarkcurrenttrack action                     
amarok:     BEGIN: virtual void MainWindow::engineStateChanged(Phonon::State, Phonon::State)                                                  
amarok:       [MainWindow] Phonon state:  0                            
amarok:     END__: virtual void MainWindow::engineStateChanged(Phonon::State, Phonon::State) - Took 8.1e-05s                                  
amarok:     BEGIN: virtual void StatusBar::engineStateChanged(Phonon::State, Phonon::State)                                                   
amarok:        LoadingState: clear text                                
amarok:     END__: virtual void StatusBar::engineStateChanged(Phonon::State, Phonon::State) - Took 0.00051s                                   
amarok:     BEGIN: virtual void Amarok::OSD::engineStateChanged(Phonon::State, Phonon::State)                                                 
amarok:     END__: virtual void Amarok::OSD::engineStateChanged(Phonon::State, Phonon::State) - Took 4.5e-05s                                 
amarok:     BEGIN: virtual void Amarok::PlayPauseAction::engineStateChanged(Phonon::State, Phonon::State)                                     
amarok:        NEWSTATE:  0 OLDSTATE:  5                               
amarok:     END__: virtual void Amarok::PlayPauseAction::engineStateChanged(Phonon::State, Phonon::State) - Took 0.0001s                      
amarok:      returning bookmarkcurrenttrack action                     
amarok:     BEGIN: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State)                                              
amarok:     END__: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State) - Took 5.7e-05s                              
amarok:   END__: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State) - Took 0.0079s                                          
amarok: END__: void EngineController::slotStateChanged(Phonon::State, Phonon::State) - Took 0.0079s                                           
amarok: BEGIN: void EngineController::slotStateChanged(Phonon::State, Phonon::State)                                                          
amarok:   [EngineController] **[WARNING!] Phonon failed to play this URL. Error:  "Cannot find demultiplexer plugin for MRL [file://media/ULOZISTE/#Hudba/EF/Give Me Beauty...Or Give Me Death!/01-ef-ett.mp3]"       ** 
amarok:   BEGIN: void Playlist::Actions::requestNextTrack()            
amarok:     [Playlist::Actions] so far so good!                        
amarok:     [Playlist::Actions] nothing more to play...                
amarok:   END__: void Playlist::Actions::requestNextTrack() - Took 7.9e-05s                                                                   
amarok:   BEGIN: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State)                                                         
amarok:     BEGIN: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State)                                              
amarok:     END__: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State) - Took 3.1e-05s                              
amarok:     BEGIN: virtual void SqlPodcastProvider::engineStateChanged(Phonon::State, Phonon::State)                                          
amarok:        NEWSTATE:  5 OLDSTATE:  0                               
amarok:     END__: virtual void SqlPodcastProvider::engineStateChanged(Phonon::State, Phonon::State) - Took 5.1e-05s                          
amarok:      returning bookmarkcurrenttrack action                     
amarok:     BEGIN: virtual void MainWindow::engineStateChanged(Phonon::State, Phonon::State)                                                  
amarok:       [MainWindow] Phonon state:  5                            
amarok:     END__: virtual void MainWindow::engineStateChanged(Phonon::State, Phonon::State) - Took 6.1e-05s                                  
amarok:     BEGIN: virtual void StatusBar::engineStateChanged(Phonon::State, Phonon::State)                                                   
amarok:     END__: virtual void StatusBar::engineStateChanged(Phonon::State, Phonon::State) - Took 3.3e-05s                                   
amarok:     [Playlist::Actions] [WARNING!] Error, can not play this track.                                                                    
amarok:     [Playlist::Actions] [WARNING!] Failure count:  2           
amarok:     BEGIN: virtual void Amarok::OSD::engineStateChanged(Phonon::State, Phonon::State)                                                 
amarok:     END__: virtual void Amarok::OSD::engineStateChanged(Phonon::State, Phonon::State) - Took 3.2e-05s                                 
amarok:     BEGIN: virtual void Amarok::PlayPauseAction::engineStateChanged(Phonon::State, Phonon::State)                                     
amarok:        NEWSTATE:  5 OLDSTATE:  0                               
amarok:     END__: virtual void Amarok::PlayPauseAction::engineStateChanged(Phonon::State, Phonon::State) - Took 5.1e-05s
amarok:      returning bookmarkcurrenttrack action
amarok:     BEGIN: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State)
amarok:     END__: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State) - Took 3.7e-05s
amarok:   END__: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State) - Took 0.0056s
amarok: END__: void EngineController::slotStateChanged(Phonon::State, Phonon::State) - Took 0.0058s
amarok: BEGIN: void CurrentTrack::dataUpdated(const QString&, const QHash<QString, QVariant>&)
amarok:    returning bookmarkcurrenttrack action
amarok: END__: void CurrentTrack::dataUpdated(const QString&, const QHash<QString, QVariant>&) - Took 0.00097s
HTTP POST:  QUrl( "http://post.audioscrobbler.com:80/np_1.2" )  "a=Ef&t=Ett&b=Give%20Me%20Beauty...%20Or%20Give%20Me%20Death%21-%28JP%20Import%29&l=241&n=0&m="
"OK"
amarok: BEGIN: void ScanManager::startIncrementalScan()
amarok:   BEGIN: QStringList ScanManager::getDirsToScan()
amarok:   END__: QStringList ScanManager::getDirsToScan() - Took 1.1s
amarok:    GOING TO SCAN:
amarok:    Scanning nothing, return.
amarok:   BEGIN: void ScanManager::writeBatchIncrementalInfoFile()
amarok:   END__: void ScanManager::writeBatchIncrementalInfoFile() - Took 0.0016s
amarok: END__: void ScanManager::startIncrementalScan() - Took 1.1s
amarok: BEGIN: void ScanManager::startIncrementalScan()
amarok:   BEGIN: QStringList ScanManager::getDirsToScan()
amarok:   END__: QStringList ScanManager::getDirsToScan() - Took 1s
amarok:    GOING TO SCAN:
amarok:    Scanning nothing, return.
amarok:   BEGIN: void ScanManager::writeBatchIncrementalInfoFile()
amarok:   END__: void ScanManager::writeBatchIncrementalInfoFile() - Took 0.0016s
amarok: END__: void ScanManager::startIncrementalScan() - Took 1s
amarok: BEGIN: void ScanManager::startIncrementalScan()
amarok:   BEGIN: QStringList ScanManager::getDirsToScan()
amarok:   END__: QStringList ScanManager::getDirsToScan() - Took 1s
amarok:    GOING TO SCAN:
amarok:    Scanning nothing, return.
amarok:   BEGIN: void ScanManager::writeBatchIncrementalInfoFile()
amarok:   END__: void ScanManager::writeBatchIncrementalInfoFile() - Took 0.0016s
amarok: END__: void ScanManager::startIncrementalScan() - Took 1s

```
I believe that the problem might be hidden in the lines I've made bold, but I don't understand a bit of it :-[

---

### Post by rbolio on 2009-11-04
IM getting the same output... found This tho "demultiplexer plugin"

maybe theres something to do there...i'll see what i can find :D


btw, do you keep your music in a different partition?

---

### Post by pumrel on 2009-11-04
You mean on that shared device? No, there's only one partition on the disk.

---

