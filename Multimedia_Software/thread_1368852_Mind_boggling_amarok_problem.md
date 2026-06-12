---
title: "Mind boggling amarok problem"
date: 2009-12-31
forum: Multimedia Software
---

### Post by booleancat on 2009-12-31
I'm completely stumped.

A few days ago, my amarok 2.2.0 installation was working perfectly. Now, I can no longer play any sound through amarok. I've tried everything from purging pulseaudio to deleting the files in ~/.kde/share/apps/amarok/  to dpkg-reconfiguring all of the relevant packages I could think of.

After some tinkering, I noticed that I can't even get the test sound to play from System Settings -> Multimedia.

I can get rhythmbox to play songs, but it won't recognize when I put in a CD (I just got an awesome CD from a friend for the holidays and very much want to hear it). I can get VLC to play the CD, but it hardlocks my computer...

When I launch amarok with the --debug flag and try to play one song, this is the output I'm receiving:

```

amarok: BEGIN: void Playlist::PrettyListView::trackActivated(const QModelIndex&) 
amarok:   BEGIN: void Playlist::Actions::play(quint64, bool)                                       
amarok:     BEGIN: void EngineController::play(const Meta::TrackPtr&, uint)                        
amarok:       [EngineController] Just a normal, boring track... :-P                                
amarok:       BEGIN: void EngineController::playUrl(const KUrl&, uint)                             
amarok:         [EngineController] URL:  "file:///home/cye/Music/A/Aceyalone/Magnificent%20City/14%20-%20A%20Beautiful%20Mine.mp3" 
amarok:         BEGIN: void EngineController::slotNewTrackPlaying(const Phonon::MediaSource&)                                      
amarok:           BEGIN: virtual void TimecodeObserver::engineNewTrackPlaying()                                                    
amarok:              curent track name:  "A Beautiful Mine"                                                                        
amarok:              Track timecodeable                                                                                            
amarok:           END__: virtual void TimecodeObserver::engineNewTrackPlaying() - Took 0.00015s                                    
amarok:            returning bookmarkcurrenttrack action                                                                           
amarok:           BEGIN: virtual void ProgressWidget::engineNewTrackPlaying()                                                      
amarok:             BEGIN: virtual void ProgressWidget::engineTrackLengthChanged(long int)                                         
amarok:                new length:  329                                                                                            
amarok:                slider enabled!                                                                                             
amarok:               BEGIN: void ProgressWidget::redrawBookmarks()                                                                
amarok:                  found  0  timecodes on this track                                                                         
amarok:               END__: void ProgressWidget::redrawBookmarks() - Took 0.0011s                                                 
amarok:             END__: virtual void ProgressWidget::engineTrackLengthChanged(long int) - Took 0.0015s                          
amarok:           END__: virtual void ProgressWidget::engineNewTrackPlaying() - Took 0.0018s                                       
amarok:           BEGIN: virtual void ProgressWidget::engineNewTrackPlaying()                                                      
amarok:             BEGIN: virtual void ProgressWidget::engineTrackLengthChanged(long int)                                         
amarok:                new length:  329                                                                                            
amarok:                slider enabled!                                                                                             
amarok:               BEGIN: void ProgressWidget::redrawBookmarks()                                                                
amarok:                  found  0  timecodes on this track                                                                         
amarok:               END__: void ProgressWidget::redrawBookmarks() - Took 0.00042s                                                
amarok:             END__: virtual void ProgressWidget::engineTrackLengthChanged(long int) - Took 0.00077s                         
amarok:           END__: virtual void ProgressWidget::engineNewTrackPlaying() - Took 0.001s                                        
amarok:           BEGIN: void Playlist::PrettyListView::scrollToActiveTrack()                                                      
amarok:             [Playlist::PrettyListView] skipping scroll? true                                                               
amarok:           END__: void Playlist::PrettyListView::scrollToActiveTrack() - Took 0.00022s
amarok:           BEGIN: virtual void Context::ContextView::engineNewTrackPlaying()
amarok:             BEGIN: virtual void CurrentEngine::message(const Context::ContextState&)
amarok:               BEGIN: void CurrentEngine::update()
amarok:               END__: void CurrentEngine::update() - Took 0.022s
amarok:             END__: virtual void CurrentEngine::message(const Context::ContextState&) - Took 0.022s
amarok:           END__: virtual void Context::ContextView::engineNewTrackPlaying() - Took 0.022s
amarok:         END__: void EngineController::slotNewTrackPlaying(const Phonon::MediaSource&) - Took 0.13s
amarok:       END__: void EngineController::playUrl(const KUrl&, uint) - Took 0.13s
amarok:     END__: void EngineController::play(const Meta::TrackPtr&, uint) - Took 0.13s
amarok:   END__: void Playlist::Actions::play(quint64, bool) - Took 0.13s
amarok: END__: void Playlist::PrettyListView::trackActivated(const QModelIndex&) - Took 0.13s
amarok: BEGIN: void EngineController::slotStateChanged(Phonon::State, Phonon::State)
amarok:   [EngineController] [WARNING!] Phonon failed to play this URL. Error:  "Cannot find demultiplexer plugin for MRL [file://home/cye/Music/A/Aceyalone/Magnificent City/14 - A Beautiful Mine.mp3]"
amarok:   BEGIN: void Playlist::Actions::requestNextTrack()
amarok:     [Playlist::Actions] so far so good!
amarok:     [Playlist::Actions] nothing more to play...
amarok:   END__: void Playlist::Actions::requestNextTrack() - Took 0.0001s
amarok:   BEGIN: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State)
amarok:     BEGIN: virtual void SqlPodcastProvider::engineStateChanged(Phonon::State, Phonon::State)
amarok:        NEWSTATE:  5 OLDSTATE:  0
amarok:     END__: virtual void SqlPodcastProvider::engineStateChanged(Phonon::State, Phonon::State) - Took 6.2e-05s
amarok:     BEGIN: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State)
amarok:     END__: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State) - Took 7.8e-05s
amarok:     BEGIN: virtual void Amarok::PlayPauseAction::engineStateChanged(Phonon::State, Phonon::State)
amarok:        NEWSTATE:  5 OLDSTATE:  0
amarok:     END__: virtual void Amarok::PlayPauseAction::engineStateChanged(Phonon::State, Phonon::State) - Took 6.5e-05s
amarok:     BEGIN: virtual void MainWindow::engineStateChanged(Phonon::State, Phonon::State)
amarok:       [MainWindow] Phonon state:  5
amarok:     END__: virtual void MainWindow::engineStateChanged(Phonon::State, Phonon::State) - Took 6.1e-05s
amarok:      returning bookmarkcurrenttrack action
amarok:      returning bookmarkcurrenttrack action
amarok:     [Playlist::Actions] [WARNING!] Error, can not play this track.
amarok:     [Playlist::Actions] [WARNING!] Failure count:  1
amarok:     BEGIN: virtual void Amarok::OSD::engineStateChanged(Phonon::State, Phonon::State)
amarok:     END__: virtual void Amarok::OSD::engineStateChanged(Phonon::State, Phonon::State) - Took 4.3e-05s
amarok:     BEGIN: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State)
amarok:     END__: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State) - Took 3.9e-05s
amarok:     BEGIN: virtual void StatusBar::engineStateChanged(Phonon::State, Phonon::State)
amarok:     END__: virtual void StatusBar::engineStateChanged(Phonon::State, Phonon::State) - Took 3.9e-05s
amarok:   END__: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State) - Took 0.045s
amarok: END__: void EngineController::slotStateChanged(Phonon::State, Phonon::State) - Took 0.046s
amarok: BEGIN: void CurrentTrack::dataUpdated(const QString&, const QHash<QString, QVariant>&)
amarok: END__: void CurrentTrack::dataUpdated(const QString&, const QHash<QString, QVariant>&) - Took 0.00067s

```Any ideas?

**EDIT** Oh yeah, I already made sure that the xine-ffmpeg, etc packages were installed.

THIS WAS WORKING 2 DAYS AGO.

---

### Post by viaciofano on 2009-12-31
have you made a note of all the changes you have made?
can you go back and unchange

---

### Post by booleancat on 2009-12-31
That's just it... The only recent changes I've made were the ones to allow me to burn mp3s through k3b, and amarok worked after those (through a reboot).

---

### Post by FloLie on 2010-01-16
Hello! I just had the same problem. The solution turned out to be quite simple: just delete (or move) the file ```
~/.xine/catalog.cache
```(I got it from here: [http://bbs.archlinux.org/viewtopic.php?pid=646903#p646903](http://bbs.archlinux.org/viewtopic.php?pid=646903#p646903))

---

