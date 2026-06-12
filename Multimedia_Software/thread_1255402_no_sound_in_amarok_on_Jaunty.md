---
title: "no sound in amarok on Jaunty"
date: 2009-09-01
forum: Multimedia Software
---

### Post by mystmaiden on 2009-09-01
I noticed someone with kubuntu had this same problem, but I wasn't sure if the fix would be the same for Jaunty. In all other instances my sound has been working fine.  I just have onboard sound.

If someone knows a workaround for Jaunty, please point me to it? Thanks
mystmaiden

---

### Post by mystmaiden on 2009-09-02
Giving this a bump. I installed the phonon backend that was recommended in another thread. Still no sound but it did stop jumping from song to song when I tried to click on a song.  In addition, now when I try to shut down amarok 2 it closes whatever webpage I happen to have open in firefox. This is so frustrating because the last version of amarok I used worked so well. :(.

running from the terminal returns this:

```
ystmaiden@hal:~$ amarok
amarok(4186) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
Object::connect: No such slot MainWindow::showStatistics() in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/MainWindow.cpp:692
Object::connect:  (receiver name: 'MainWindow')
QLayout: Attempting to add QLayout "" to MainWindow "MainWindow", which already has a layout
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
amarok(4186) Plasma::Applet::save: saving to "1"
amarok(4186) Context::ContextView::setContainment: "" Line:  599
amarok(4186) Plasma::ThemePrivate::config: using theme for app "amarok"
amarok(4186) Plasma::Applet::save: saving to "2"
amarok(4186) Plasma::Applet::save: saving to "3"
amarok(4186) Plasma::Applet::save: saving to "4"
amarok(4186) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(4186) Context::ColumnContainment::insertInGrid: "" Line:  603
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
Object::connect: No such slot FileBrowser::Widget::setDir( const QString& ) in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/browsers/filebrowser/FileBrowser.cpp:112
Object::connect:  (sender name:   'KBookmarkHandler')
Object::connect:  (receiver name: 'FileBrowser::Widget')
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
amarok(4186) MagnatuneConfig::load: load
amarok(4186) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(4186) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
mystmaiden@hal:~$ amarok(4186) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated


```

Found this thread [http://ubuntuforums.org/showthread.php?t=1138252](http://ubuntuforums.org/showthread.php?t=1138252) . I've done everything in it, amarok 2 is still dead silent.

---

### Post by mystmaiden on 2009-09-05
I've run out of ideas.. anyone?

mystmaiden

---

### Post by mystmaiden on 2009-09-07
one last bump. Any help would be appreciated.

thank you,
mystmaiden

---

### Post by mystmaiden on 2009-09-08
Not sure what I did wrong here, maybe I should have posted this on one of the other threads. For now my solution - dump amarok 2 and go to rhythmbox. Not what I wanted but at least I have music. I can only think that I either did something wrong with xine or its a problem with my hardware that has made amarok 2 a no-go for me. I would like to see things working a little better than this before they are made a part of Ubuntu though.

---

### Post by ytene on 2009-09-09
Mystmaiden,

I read your post with interest and for what it's worth, I don't think you've done anything wrong with Amarok 2. 

I've been working with Jaunty on an Acer Revo - one of those baby systems. Like you, I could not get Amarok to work. It launches and the main screen appears. I can index my music library [ which in my case is merely an iTunes library on a network-connected Time Capsule ], but any attempt to play the AC4 [lossless] encoded material just didn't work. 

Sometimes the progress bar in the main window would scoot quickly from the start to the end of the track [ in say a second or so ] and on other occasions nothing would apparently happen.

I've also experimented with other music players and like you I've been able to get Rhythmbox to work quite well. [ I do get rare dropouts during playback, but I am attributing these to the modest performance of the Revo and not the player ].

If we have any moderators or technical specialists tracking this post, I'll be happy to work with you on diagnostics for Amarok, but not being the most technical person in the world, you're going to have to point me in the right direction...

Best Regards

C

---

### Post by archcynic on 2009-11-01
I've just done a fresh install of Karmic Koala (9.10) and the Amarok package (ver 2.2.0) from the Ubuntu repository produced no sound.

Sound magically appeared when I installed to following package

libxine-ffmpeg

It must have been missed off the Amarok dependency list.

Hope this helps...

---

### Post by akamaleldin on 2009-12-07
> **archcynic said:**
> I've just done a fresh install of Karmic Koala (9.10) and the Amarok package (ver 2.2.0) from the Ubuntu repository produced no sound.

Sound magically appeared when I installed to following package

libxine-ffmpeg

It must have been missed off the Amarok dependency list.

Hope this helps...

It helps perfectly well :)
Exactly what happened to me too. Thanks for your help.

---

### Post by mystmaiden on 2009-12-22
Thanks, unfortunately for me (running jaunty) installation of said file didn't seem to help at all so I'm still using Rhythmbox.  Maybe when I decide to upgrade to Karmic that'll be fixed but right now most stuff is working so I hate to move on! Heh, I'm not exactly adventuresome of late :)

---

