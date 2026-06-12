---
title: "amarok crashes after scripts are installed"
date: 2009-10-12
forum: Multimedia Software
---

### Post by junglejuice on 2009-10-12
hi there 
i use both kubuntu and ubuntu studio and have been running amarok on both environments without a probelm. i decided to install some scripts with amarok's scripts manager and the scripts installed sucessfully without any problems (or none that were apparent to me), amarok then suggested that i restart amarok in order for me to use the newly installed scripts. i did so, but when i tried to restart amarok it crashed and continues to do so. so amarok is no longer working for me on either kubuntu or ubuntu studio. i tried removing the contents of the scripts directory under /usr/share/kde4/apps/amarok/scripts/ but that didn't work so i put the contents back.
when i run amarok through terminal i get this output
```
lyndon@lyndon-desktop:~$ amarok
amarok(32484) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
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
amarok(32484) Plasma::Applet::save: saving to "1"
amarok(32484) Context::ContextView::setContainment: "" Line:  599
amarok(32484) Plasma::ThemePrivate::config: using theme for app "amarok"
amarok(32484) Plasma::Applet::save: saving to "2"
amarok(32484) Plasma::Applet::save: saving to "3"
amarok(32484) Plasma::Applet::save: saving to "4"
amarok(32484) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(32484) Context::ColumnContainment::insertInGrid: "" Line:  603
amarok(32484) Context::ColumnContainment::insertInGrid: "" Line:  603
amarok(32484) LyricsApplet::init: Loading theme file:  "/usr/share/kde4/apps/amarok/images/web_applet_background.svg"
amarok(32484) Context::ColumnContainment::insertInGrid: "" Line:  603
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
amarok(32484) MagnatuneConfig::load: load
lyndon@lyndon-desktop:~$ amarok(32484) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(32484) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(32484) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
amarok(32484) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
KCrash: Application 'amarok' crashing...
sock_file=/home/lyndon/.kde/socket-lyndon-desktop/kdeinit4__0


```
is there a way of disabling scripts to fix this problem? cause i'd rather just have a working version of amarok, i don't really care about the new scripts that i installed, especially if they prevent me form using amarok (which i think is a totally awesome player).any help that anyone can offer is greatly appreciated. regards
jj

---

### Post by junglejuice on 2009-10-12
sorry i think i forgot to include some critical info ...
i'm using ubuntu studio 9.04 and amarok ver 2:2.0.2mysql5.1.30-0ubuntu3 (as it is stated in synaptic) also i cannot tell you which scripts i installed that caused the problem as i can't open amarok to check what scripts i have installed (and my memory fails me)
not to beg/plead or anything like that but i'd really like to get amarok fixed so i can resume my normal existence..
thanks,big time if you can help me :)

---

