---
title: "Amarok will not open/start"
date: 2009-04-05
forum: Multimedia Software
---

### Post by Christian Alder on 2009-04-05
Hey all.

I installed Amarok recently, and it was working fine apart for the fact I had no sound coming out of it. Last night I was able to fix this, and things were running smooth.

Today I wake up, switch on the computer, and when I try to open Amarok nothing happens. The icon will appear in the system tray, but whenever I put my mouse over it, I am shown that it is still doing something (The little loading icon is shown for the mouse pointer) - Indicating to me, that it just crashed.

From there, I can't do anything, clicking wont effect it, and I am unable to close it (Well I managed eventually buy grabbing the PID from terminal and using the kill command on it)

I decided to run the application from the terminal, to see what would come up... I don't know if this can help someone determine what is going wrong?

```
amarok(14526) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
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
amarok(14526) Plasma::Applet::save: saving to "1"
amarok(14526) Context::ContextView::setContainment: "" Line:  599
amarok(14526) Plasma::ThemePrivate::config: using theme for app "amarok"
amarok(14526) Plasma::Applet::save: saving to "2"
amarok(14526) Plasma::Applet::save: saving to "3"
amarok(14526) Plasma::Applet::save: saving to "4"
amarok(14526) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(14526) Context::ColumnContainment::insertInGrid: "" Line:  603
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
<unknown program name>(14525)/: Communication problem with  "amarok" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." " 
```

Any help on the matter would be greatly appreciated.

Thank You :cool:

---

