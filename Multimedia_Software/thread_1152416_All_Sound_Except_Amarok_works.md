---
title: "All Sound Except Amarok works?"
date: 2009-05-07
forum: Multimedia Software
---

### Post by mattlach on 2009-05-07
Hey all,

I've got an odd problem.   My system sound server appears to be working well, and sound works in pretty much everything, including movie player, flash, etc. etc., but my primary audio player which I use for everything - Amarok complains of this when I start it up:

[[img]http://farm4.static.flickr.com/3658/3510990857_86f3674135_o.jpg[/img]](http://www.flickr.com/photos/mattlach/3510990857/)

I started Amarok from the terminal to see if it spit out any error messages of note, but I am having a difficult time interpreting it.

Here it is:

```
matt@matt:~$ amarok
amarok(4666) Phonon::KdePlatformPlugin::createBackend: using backend:  "GStreamer"
amarok(4666) KToolInvocation::klauncher: klauncher not running... launching kdeinit
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
kdeinit4: preparing to launch /usr/bin/kded4
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kded(4680) KDEDModule::setModuleName: registerObject() successful for  "kdedglobalaccel"
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
amarok(4666) Plasma::Applet::save: saving to "1"
amarok(4666) Context::ContextView::setContainment: "" Line:  599
amarok(4666) Plasma::ThemePrivate::config: using theme for app "amarok"
amarok(4666) Plasma::Applet::save: saving to "2"
amarok(4666) Plasma::Applet::save: saving to "3"
amarok(4666) Plasma::Applet::save: saving to "4"
amarok(4666) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(4666) Context::ColumnContainment::insertInGrid: "" Line:  603
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
amarok(4666) KNetworkAccessManager::createRequest: GetOperation:  QUrl( "http://ws.audioscrobbler.com/2.0/?api_key=402d3ca8e9bc9d3cf9b85e1202944ca5&api_sig=81c1a3db753f2671e658492dec480a70&authToken=e8cf26b36bd7d19ef111626dd1e74282&method=auth.getMobileSession&sk=&username=mattlach&api_sig=38c13766bdfbf69478ed3d0bd11f9a86" )
amarok(4666) KNetworkAccessManager::createRequest: GetOperation:  QUrl( "http://ws.audioscrobbler.com/2.0/?api_key=402d3ca8e9bc9d3cf9b85e1202944ca5&method=user.getNeighbours&sk=&user=mattlach&api_sig=a33953cd7c1c11cf6672be78b3663967" )
amarok(4666) KNetworkAccessManager::createRequest: GetOperation:  QUrl( "http://ws.audioscrobbler.com/2.0/?api_key=402d3ca8e9bc9d3cf9b85e1202944ca5&method=user.getFriends&sk=&user=mattlach&api_sig=ffba780aa7d34696745328bebee11f30" )
Couldn't resolve property: linearGradient5167
link XMLID_9_ hasn't been detected!
Couldn't resolve property: linearGradient3563
link XMLID_9_ hasn't been detected!
link XMLID_9_ hasn't been detected!
link XMLID_9_ hasn't been detected!
matt@matt:~$ kdeinit4: preparing to launch 
kdeinit4: preparing to launch 
kdeinit4: preparing to launch 
kdeinit4: preparing to launch 
kdeinit4: preparing to launch 
amarok(4666) DNSSD::RemoteService::resolveAsync: DNSSD::RemoteService(0x1d5c800) :Starting resolve of :  "Erin Broderick’s Music"   "_daap._tcp"   "local"
amarok(4666) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(4666) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(4666) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kio_http_cache_cleaner
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KDEDModule::setModuleName: registerObject() successful for  "kcookiejar"
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kio_http_cache_cleaner
kio_http_cache_cleaner: Already running!
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
amarok(4666) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
kded(4680) KDEDModule::setModuleName: registerObject() successful for  "ktimezoned"
amarok(4666) KNetworkReply::setMimeType: "text/xml"
":" 
  QUrl( "" )  
 "<?xml version="1.0" encoding="utf-8"?>
<lfm status="failed">
    <error code="13">Invalid method signature supplied</error></lfm>" 
amarok(4666) KNetworkReply::setMimeType: "text/xml"
amarok(4666) KNetworkReply::setMimeType: "text/xml"
QString::arg: Argument missing: Amarok - No track playing., 0:00
QString::arg: Argument missing: Amarok - No track playing., 0:00
QString::arg: Argument missing: Amarok - No track playing., 0:00
kdeinit4: preparing to launch 
QString::arg: Argument missing: Amarok - No track playing., 0:00
QString::arg: Argument missing: Amarok - No track playing., 0:00
kdeinit4: preparing to launch 
QString::arg: Argument missing: Amarok - No track playing., 0:00
QString::arg: Argument missing: Amarok - No track playing., 0:00
kdeinit4: preparing to launch 
QString::arg: Argument missing: Amarok - No track playing., 0:00
QString::arg: Argument missing: Amarok - No track playing., 0:00
kdeinit4: preparing to launch 
QString::arg: Argument missing: Amarok - No track playing., 0:00
QString::arg: Argument missing: Amarok - No track playing., 0:00
kdeinit4: preparing to launch 
amarok(4666) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(4666) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
<unknown program name>(4675)/ KStartupInfo::createNewStartupId: creating:  "matt;1241740663;326503;4675_TIME0" : "unnamed app"
kbuildsycoca4 running...
kbuildsycoca4(5494) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/audio/x-sbc.xml" 
kbuildsycoca4(5494) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-vmware-vm.xml" 
kbuildsycoca4(5494) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-hcidump.xml" 
kbuildsycoca4(5494) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-vmware-vmfoundry.xml" 
kbuildsycoca4(5494) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-vmware-team.xml" 
kbuildsycoca4(5494) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-vmware-vmdisk.xml" 
kbuildsycoca4(5494) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-pem-key.xml" 
kbuildsycoca4(5494) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-vmware-snapshot.xml" 
kbuildsycoca4(5494) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-ssh-key.xml" 
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
<unknown program name>(4675)/ KStartupInfo::createNewStartupId: creating:  "matt;1241740688;47823;4675_TIME0" : "unnamed app"
kbuildsycoca4 running...
amarok(4666) Context::ContextView::clear: "" Line:  165
amarok(4666) Context::ContextView::clear: "" Line:  165
amarok(4666) Context::ContextView::clear: "" Line:  165
amarok(4666) Context::ContextView::clear: "" Line:  165
kded(4680) KDEDModule::setModuleName: registerObject() successful for  "phononserver"
kdeinit4: preparing to launch /usr/bin/knotify4
kdeinit4: preparing to launch 
kdeinit4: preparing to launch 
kdeinit4: preparing to launch 
kdeinit4: preparing to launch 
kdeinit4: preparing to launch 
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"
kded(4680) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kded/networkstatus.desktop not found"

```

Any ideas what could be wrong here?  I've tried everything I can think of, including reinstalling Amarok, asoundconf-gtk alsa-oss libasound2 libasound2-plugins padevchooser gstreamer0.10-pulseaudio ubuntu-restricted-extras.

Any help would be appreciated!

Thanks,
Matt

---

### Post by mattlach on 2009-05-07
Could it have something to do with that this gstreamer plugins package is grayed out and not installed?

[[img]http://farm4.static.flickr.com/3395/3490061692_18c944d414_o.jpg[/img]](http://www.flickr.com/photos/mattlach/3490061692/)

---

### Post by mc4man on 2009-05-07
I don't have jaunty but was using the live cd yesterday and tried out amarok2 ( had sound

When I installed amarok i also installed libxine1-ffmpeg and phonon-backend-xine 

Maybe ck. on those 2 (particularly the latter

---

### Post by mattlach on 2009-05-07
> **mc4man said:**
> I don't have jaunty but was using the live cd yesterday and tried out amarok2 ( had sound

When I installed amarok i also installed libxine1-ffmpeg and phonon-backend-xine 

Maybe ck. on those 2 (particularly the latter

Thank you very much, the phonon-backend-xine did the trick!

---

