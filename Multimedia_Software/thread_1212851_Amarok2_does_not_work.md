---
title: "Amarok2 does not work"
date: 2009-07-14
forum: Multimedia Software
---

### Post by roida on 2009-07-14
Hello,

My system's sound works totally fine for every application, except for Amarok. I have been looking around for a while but i still cannot get it working.

Basically, when i play a file, nothing happen. If i press for few time, i will have a small context box opening on the bottum left saying "Too many errors occured in the playlist" or something similar...

Could someone help me?

Thanks!

---

### Post by SyL on 2009-07-14
Do you have any error in the output?
Open a terminal and type ```
amarok -d
```

---

### Post by SyL on 2009-07-14
BTW which version of ubuntu and amarok are you using?

---

### Post by roida on 2009-07-14
Hello,

My version of Ubuntu is 9.04 Jaunty Jackalope 
My version of Amarok is: > Qt: 4.5.0
KDE: 4.2.2 (KDE 4.2.2)
Amarok: 2.0.2


The output is:
```

amarok: BEGIN: void EngineController::playPause() 
amarok:   [EngineController] PlayPause: phonon state 0 
amarok: BEGIN: void EngineController::play() 
amarok: BEGIN: void Playlist::Actions::play(quint64, bool) 
amarok: BEGIN: void EngineController::play(const Meta::TrackPtr&, uint) 
amarok: BEGIN: void EngineController::playUrl(const KUrl&, uint) 
amarok: BEGIN: void EngineController::slotStopFadeout() 
amarok: END__: void EngineController::slotStopFadeout() - Took 4.5e-05s 
amarok:           [EngineController] URL:  "file:///home/roida/Musique/Chet%20Baker/Chet/01%20-%20Chet%20Baker%20-%20Alone%20Together.mp3" 
amarok: BEGIN: void EngineController::slotStateChanged(Phonon::State, Phonon::State) 
amarok: BEGIN: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State) 
amarok: BEGIN: virtual void Context::ContextView::engineStateChanged(Phonon::State, Phonon::State) 
amarok: BEGIN: virtual void CurrentEngine::message(const Context::ContextState&) 
amarok: END__: virtual void CurrentEngine::message(const Context::ContextState&) - Took 6e-05s 
amarok: END__: virtual void Context::ContextView::engineStateChanged(Phonon::State, Phonon::State) - Took 0.00015s 
amarok: BEGIN: virtual void Amarok::OSD::engineStateChanged(Phonon::State, Phonon::State) 
amarok: END__: virtual void Amarok::OSD::engineStateChanged(Phonon::State, Phonon::State) - Took 0.00011s 
amarok: BEGIN: virtual void MainWindow::engineStateChanged(Phonon::State, Phonon::State) 
amarok:                 [MainWindow] Phonon state:  1 
amarok: END__: virtual void MainWindow::engineStateChanged(Phonon::State, Phonon::State) - Took 0.00012s 
amarok: BEGIN: virtual void Amarok::PlayPauseAction::engineStateChanged(Phonon::State, Phonon::State) 
amarok:                  NEWSTATE:  1 OLDSTATE:  0 
amarok: END__: virtual void Amarok::PlayPauseAction::engineStateChanged(Phonon::State, Phonon::State) - Took 0.00013s 
amarok: BEGIN: virtual void StatusBar::engineStateChanged(Phonon::State, Phonon::State) 
amarok: END__: virtual void StatusBar::engineStateChanged(Phonon::State, Phonon::State) - Took 0.00014s 
amarok: BEGIN: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State) 
amarok: END__: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State) - Took 5e-05s 
amarok: END__: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State) - Took 0.003s 
amarok: END__: void EngineController::slotStateChanged(Phonon::State, Phonon::State) - Took 0.0031s 
amarok: BEGIN: void EngineController::slotNewTrackPlaying(const Phonon::MediaSource&) 
amarok: BEGIN: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State) 
amarok: BEGIN: virtual void Context::ContextView::engineStateChanged(Phonon::State, Phonon::State) 
amarok: END__: virtual void Context::ContextView::engineStateChanged(Phonon::State, Phonon::State) - Took 4.4e-05s 
amarok: BEGIN: virtual void Amarok::OSD::engineStateChanged(Phonon::State, Phonon::State) 
amarok: END__: virtual void Amarok::OSD::engineStateChanged(Phonon::State, Phonon::State) - Took 0.00023s 
amarok: BEGIN: virtual void MainWindow::engineStateChanged(Phonon::State, Phonon::State) 
amarok:                 [MainWindow] Phonon state:  0 
amarok: END__: virtual void MainWindow::engineStateChanged(Phonon::State, Phonon::State) - Took 0.00017s 
amarok: BEGIN: virtual void Amarok::PlayPauseAction::engineStateChanged(Phonon::State, Phonon::State) 
amarok:                  NEWSTATE:  0 OLDSTATE:  0 
amarok: END__: virtual void Amarok::PlayPauseAction::engineStateChanged(Phonon::State, Phonon::State) - Took 0.0002s 
amarok: BEGIN: virtual void StatusBar::engineStateChanged(Phonon::State, Phonon::State) 
amarok:                  LoadingState: clear text 
amarok: END__: virtual void StatusBar::engineStateChanged(Phonon::State, Phonon::State) - Took 0.0012s 
amarok: BEGIN: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State) 
amarok: END__: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State) - Took 9.9e-05s 
amarok: END__: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State) - Took 0.0051s 
amarok: BEGIN: virtual void TrackToolTip::engineNewTrackPlaying() 
amarok: BEGIN: void TrackToolTip::setTrack() 
amarok: BEGIN: void TrackToolTip::clear() 
QString::arg: Argument missing: Amarok - No track playing., 0:00
amarok: END__: void TrackToolTip::clear() - Took 0.0003s 
amarok: END__: void TrackToolTip::setTrack() - Took 0.0019s 
amarok: END__: virtual void TrackToolTip::engineNewTrackPlaying() - Took 0.0021s 
amarok: BEGIN: virtual void ProgressWidget::engineTrackLengthChanged(long int) 
amarok:                new length:  412 
amarok:                slider enabled! 
amarok: END__: virtual void ProgressWidget::engineTrackLengthChanged(long int) - Took 0.00039s 
amarok: END__: void EngineController::slotNewTrackPlaying(const Phonon::MediaSource&) - Took 0.013s 
amarok: BEGIN: void EngineController::slotStateChanged(Phonon::State, Phonon::State) 
amarok: BEGIN: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State) 
amarok: END__: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State) - Took 4.5e-05s 
amarok: END__: void EngineController::slotStateChanged(Phonon::State, Phonon::State) - Took 0.00013s 
amarok: END__: void EngineController::playUrl(const KUrl&, uint) - Took 0.018s 
amarok: END__: void EngineController::play(const Meta::TrackPtr&, uint) - Took 0.018s 
amarok: END__: void Playlist::Actions::play(quint64, bool) - Took 0.018s 
amarok: END__: void EngineController::play() - Took 0.018s 
amarok: END__: void EngineController::playPause() - Took 0.019s 
amarok: BEGIN: void EngineController::slotNewTrackPlaying(const Phonon::MediaSource&) 
amarok: BEGIN: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State) 
amarok: END__: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State) - Took 5.3e-05s 
amarok: BEGIN: virtual void TrackToolTip::engineNewTrackPlaying() 
amarok: BEGIN: void TrackToolTip::setTrack() 
amarok: BEGIN: void TrackToolTip::clear() 
QString::arg: Argument missing: Amarok - No track playing., 0:00
amarok: END__: void TrackToolTip::clear() - Took 0.00034s 
amarok: END__: void TrackToolTip::setTrack() - Took 0.0018s 
amarok: END__: virtual void TrackToolTip::engineNewTrackPlaying() - Took 0.002s 
amarok: BEGIN: virtual void ProgressWidget::engineTrackLengthChanged(long int) 
amarok:      new length:  412 
amarok:      slider enabled! 
amarok: END__: virtual void ProgressWidget::engineTrackLengthChanged(long int) - Took 0.00013s 
amarok:   [Playlist::Actions] [WARNING!] engineNewTrackPlaying: "Alone Together" does not match what the playlist controller thought it should be 
amarok: END__: void EngineController::slotNewTrackPlaying(const Phonon::MediaSource&) - Took 0.018s 
kdeinit4: preparing to launch 
amarok: BEGIN: void EngineController::slotStateChanged(Phonon::State, Phonon::State) 
amarok:   [EngineController] [WARNING!] Phonon failed to play this URL. Error:  "" 
amarok: BEGIN: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State) 
amarok: BEGIN: virtual void Context::ContextView::engineStateChanged(Phonon::State, Phonon::State) 
amarok: END__: virtual void Context::ContextView::engineStateChanged(Phonon::State, Phonon::State) - Took 4.7e-05s 
amarok: BEGIN: virtual void Amarok::OSD::engineStateChanged(Phonon::State, Phonon::State) 
amarok: END__: virtual void Amarok::OSD::engineStateChanged(Phonon::State, Phonon::State) - Took 0.00013s 
amarok: BEGIN: virtual void MainWindow::engineStateChanged(Phonon::State, Phonon::State) 
amarok:       [MainWindow] Phonon state:  5 
amarok: END__: virtual void MainWindow::engineStateChanged(Phonon::State, Phonon::State) - Took 0.00036s 
amarok: BEGIN: virtual void Amarok::PlayPauseAction::engineStateChanged(Phonon::State, Phonon::State) 
amarok:        NEWSTATE:  5 OLDSTATE:  0 
amarok: END__: virtual void Amarok::PlayPauseAction::engineStateChanged(Phonon::State, Phonon::State) - Took 7.8e-05s 
amarok: BEGIN: virtual void StatusBar::engineStateChanged(Phonon::State, Phonon::State) 
amarok: END__: virtual void StatusBar::engineStateChanged(Phonon::State, Phonon::State) - Took 4.4e-05s 
amarok: BEGIN: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State) 
amarok: END__: virtual void ProgressWidget::engineStateChanged(Phonon::State, Phonon::State) - Took 4.5e-05s 
amarok:     [Playlist::Actions] [WARNING!] Error, can not play this track. 
amarok:     [Playlist::Actions] [WARNING!] Failure count:  3 
amarok: END__: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State) - Took 0.003s 
amarok: END__: void EngineController::slotStateChanged(Phonon::State, Phonon::State) - Took 0.0032s 
amarok: BEGIN: void CurrentEngine::stoppedState() 
amarok: END__: void CurrentEngine::stoppedState() - Took 0.00045s 
amarok: BEGIN: void Albums::dataUpdated(const QString&, const QHash<QString, QVariant>&) 
amarok: END__: void Albums::dataUpdated(const QString&, const QHash<QString, QVariant>&) - Took 6.3e-05s 
amarok: BEGIN: void CurrentTrack::dataUpdated(const QString&, const QHash<QString, QVariant>&) 
amarok(5926) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok: END__: void CurrentTrack::dataUpdated(const QString&, const QHash<QString, QVariant>&) - Took 0.00033s 
amarok:  Initialized thread, count== 5 
amarok: BEGIN: void CurrentEngine::resultReady(const QString&, const Meta::TrackList&) 
amarok: END__: void CurrentEngine::resultReady(const QString&, const Meta::TrackList&) - Took 0.00015s 
amarok: BEGIN: void CurrentEngine::setupTracksData() 
amarok: END__: void CurrentEngine::setupTracksData() - Took 0.00012s 
amarok: BEGIN: void CurrentEngine::resultReady(const QString&, const Meta::AlbumList&) 
amarok: END__: void CurrentEngine::resultReady(const QString&, const Meta::AlbumList&) - Took 5.1e-05s 
amarok: BEGIN: void Albums::dataUpdated(const QString&, const QHash<QString, QVariant>&) 
amarok:    Received 5 albums 
amarok: END__: void Albums::dataUpdated(const QString&, const QHash<QString, QVariant>&) - Took 0.012s 
amarok: BEGIN: void CurrentTrack::dataUpdated(const QString&, const QHash<QString, QVariant>&) 
amarok(5926) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok: END__: void CurrentTrack::dataUpdated(const QString&, const QHash<QString, QVariant>&) - Took 0.00017s 
amarok: BEGIN: virtual void Albums::constraintsEvent(Plasma::Constraints) 
amarok:    Updating constraints for  -2147483648  album rows 
amarok: END__: virtual void Albums::constraintsEvent(Plasma::Constraints) - Took 9.8e-05s 
amarok: BEGIN: virtual void CurrentTrack::constraintsEvent(Plasma::Constraints) 
amarok: END__: virtual void CurrentTrack::constraintsEvent(Plasma::Constraints) - Took 0.00059s 

```


This drive me crazy...

Thanks!!

---

### Post by SyL on 2009-07-14
I had a quite similar issue in the past with Jaunty.
Once i installed libxine1-ffmpeg and phonon-backend-xine it worked fine.

Also check either all codecs are install?
You could also try to install ubuntu-restricted-extras ...

---

### Post by roida on 2009-07-14
Thanks a lot SyL!!!
This is now working now :-)

The problem was not related to the codec but to libxine1-ffmpeg
Thnaks again

---

### Post by SyL on 2009-07-14
> **roida said:**
> Thanks a lot SyL!!!
This is now working now :-)

The problem was not related to the codec but to libxine1-ffmpeg
Thnaks again

Enjoy Chet Baker ;-)

---

### Post by roida on 2009-07-27
> **SyL said:**
> Enjoy Chet Baker ;-)

Thank u!
How do you know that?

---

### Post by SyL on 2009-07-27
> **roida said:**
> Thank u!
How do you know that?

Just looked at the logs you have posted:
```
amarok:           [EngineController] URL:  "file:///home/roida/Musique/Chet%20Baker/Chet/01%20-%20Chet%20Baker%20-%20Alone%20Together.mp3" 

```

---

### Post by Jeffa on 2009-07-30
This fixed the problem for me too. Thank you community!

---

### Post by SyL on 2009-08-03
> **Jeffa said:**
> This fixed the problem for me too. Thank you community!


Good to know!
Thanks :-)

---

### Post by a3uge on 2009-08-08
I have the same exact problem, except mine only works in sudo. HELP!

---

### Post by SyL on 2009-08-08
> **a3uge said:**
> I have the same exact problem, except mine only works in sudo. HELP!


What are the output logs?
Did you install the packages libxine1-ffmpeg and phonon-backend-xine?

---

