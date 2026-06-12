---
title: "Amarok Audio Trouble"
date: 2009-09-21
forum: Multimedia Software
---

### Post by Fernando Hernandez on 2009-09-21
When Amarok came pre-installed on my Kubuntu system, I was very pleased.  However, as of the past few weeks or so, I'm not getting any audio output from it.  It doesn't matter how many times I restart the program or my system.  All other audio works fine - I can go online and watch videos on YouTube without any sound issues, and VLC Media Player is giving perfect audio (I like VLC as a video player, though; I'd really like to fix Amarok if possible for music).  The only problem is Amarok, and I don't know why, nor do I know how to fix it.  I even tried uninstalling and then reinstalling it via the package manager...no changes.

Is there a way to fix this problem, or at least a way to remove Amarok and have it not remember any of my settings, playlists, etc, so that I could possibly reinstall it from scratch?  I could always find another music player, I know, but I really enjoyed Amarok's functionality and if I could fix it that'd be nice.

Thanks!!  :)

---

### Post by Fernando Hernandez on 2009-09-23
No one? :(

---

### Post by Fernando Hernandez on 2009-09-25
&#65279;When I run Amarok via the terminal it gives me this output if it helps anyone...I'd really like to fix it, I've tried Ryhthmbox, Banshee, Exiale...I don't like any of them as much as Amarok, and I'd really like to know what's wrong with it...
 
fernando@Laptop:~$ amarok
 qUncompress: Z_DATA_ERROR: Input data is corrupted
 amarok(1442) Phonon::KdePlatformPlugin::createBackend: using backend: "Xine"
 PTP: Opening session 
Object::connect: No such slot MainWindow::showStatistics() in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/MainWindow.cpp:692 
Object::connect: (receiver name: 'MainWindow') 
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
amarok(1442) Plasma::Applet::save: saving to "1" 
amarok(1442) Context::ContextView::setContainment: "" Line: 599 
amarok(1442) Plasma::ThemePrivate::config: using theme for app "amarok" 
amarok(1442) Plasma::Applet::save: saving to "2" 
amarok(1442) Plasma::Applet::save: saving to "3" 
amarok(1442) Plasma::Applet::save: saving to "4" 
amarok(1442) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated 
amarok(1442) Context::ColumnContainment::insertInGrid: "" Line: 603 
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
Object::connect: (sender name: 'KBookmarkHandler') 
Object::connect: (receiver name: 'FileBrowser::Widget') 
link XMLID_7_ hasn't been detected! 
link XMLID_7_ hasn't been detected! 
Couldn't resolve property: radialGradient3986 
link XMLID_7_ hasn't been detected! 
link XMLID_7_ hasn't been detected! 
Couldn't resolve property: radialGradient3986 
amarok(1442) KNetworkAccessManager::createRequest: GetOperation: QUrl( "http://ws.audioscrobbler.com/2.0/?api_key=402d3ca8e9bc9d3cf9b85e1202944ca5&api_sig=04031431d9cf2ee2483b544f8ea588a4&authToken=679c432f975040e738ad92066688e37d&method=auth.getMobileSession&sk=&username=sg2chibitiger&api_sig=0080e883c3f3b678d9c0ca07d312c9a8" ) 
amarok(1442) KNetworkAccessManager::createRequest: GetOperation: QUrl( "http://ws.audioscrobbler.com/2.0/?api_key=402d3ca8e9bc9d3cf9b85e1202944ca5&method=user.getNeighbours&sk=&user=sg2chibitiger&api_sig=5d0f18c3d60cfb85488bffa4928bc6f1" ) 
amarok(1442) KNetworkAccessManager::createRequest: GetOperation: QUrl( "http://ws.audioscrobbler.com/2.0/?api_key=402d3ca8e9bc9d3cf9b85e1202944ca5&method=user.getFriends&sk=&user=sg2chibitiger&api_sig=a5107ead0abb468047a29074bf464b63" ) 
Couldn't resolve property: linearGradient5167 
link XMLID_9_ hasn't been detected! 
Couldn't resolve property: linearGradient3563 
link XMLID_9_ hasn't been detected! 
link XMLID_9_ hasn't been detected! 
link XMLID_9_ hasn't been detected! 
fernando@Laptop:~$ amarok(1442) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated 
amarok(1442) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated 
amarok(1442) DNSSD::RemoteService::resolveAsync: DNSSD::RemoteService(0xc7e1a9 :Starting resolve of : "Kendra&#8217;s Library" "_daap._tcp" "local" 
qUncompress: Input data is corrupted 
qUncompress: Input data is corrupted 
amarok(1442) CoverFetcher::CoverFetcher: "" 
qUncompress: Input data is corrupted 
qUncompress: Input data is corrupted 
qUncompress: Input data is corrupted 
qUncompress: Input data is corrupted 
QPainter::begin: Cannot paint on a null pixmap 
QPainter::begin: Cannot paint on a null pixmap 
QPainter::begin: Cannot paint on a null pixmap 
QPainter::begin: Cannot paint on a null pixmap 
QPainter::begin: Cannot paint on a null pixmap 
qUncompress: Input data is corrupted 
amarok(1442) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated 
qUncompress: Input data is corrupted 
amarok(1442) KNetworkReply::setMimeType: "text/xml" 
amarok(1442) KNetworkReply::setMimeType: "text/xml" 
amarok(1442) KNetworkReply::setMimeType: "text/xml" 
":" 
QUrl( "" ) 
"<?xml version="1.0" encoding="utf-8"?> 
<lfm status="failed"> 
<error code="13">Invalid method signature supplied</error></lfm>" 

fernando@Laptop:~$ link XMLID_9_ hasn't been detected! 
> Couldn't resolve property: linearGradient3563 
link: extra operand `resolve' 
Try `link --help' for more information. 
fernando@Laptop:~$ link XMLID_9_ hasn't been detected! 
> link XMLID_9_ hasn't been detected! 
link: extra operand `been' 
Try `link --help' for more information. 
fernando@Laptop:~$ link XMLID_9_ hasn't been detected! 
> fernando@Laptop:~$ amarok(1442) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated 
> amarok(1442) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated 
> amarok(1442) DNSSD::RemoteService::resolveAsync: DNSSD::RemoteService(0xc7e1a9 :Starting resolve of : "Kendra&#8217;s Library" "_daap._tcp" "local" 
> qUncompress: Input data is corrupted 
> qUncompress: Input data is corrupted 
> amarok(1442) CoverFetcher::CoverFetcher: "" 
> qUncompress: Input data is corrupted 
> qUncompress: Input data is corrupted
 > qUncompress: Input data is corrupted
 > qUncompress: Input data is corrupted
 > QPainter::begin: Cannot paint on a null pixmap
 > QPainter::begin: Cannot paint on a null pixmap
 > QPainter::begin: Cannot paint on a null pixmap
 > QPainter::begin: Cannot paint on a null pixmap
 > QPainter::begin: Cannot paint on a null pixmap
 > qUncompress: Input data is corrupted
 > amarok(1442) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
 > qUncompress: Input data is corrupted
 > amarok(1442) KNetworkReply::setMimeType: "text/xml"
 > amarok(1442) KNetworkReply::setMimeType: "text/xml"
 > amarok(1442) KNetworkReply::setMimeType: "text/xml"
 > ":"
 > QUrl( "" )
 > "<?xml version="1.0" encoding="utf-8"?>
 > <lfm status="failed">
 > <error code="13">Invalid method signature supplied</error></lfm>"

---

### Post by Nick Brohman on 2009-09-26
Fernando you might find an alternative at  [http://www.osalt.com](http://www.osalt.com)

There are some interesting players available there.

I just want Amarok 1.4.9.

Nicko

---

