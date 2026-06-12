---
title: "Amarok problem on Ubuntu 9.10 beta"
date: 2009-10-17
forum: Multimedia Software
---

### Post by KriZo on 2009-10-17
I just installed the Ubuntu 9.10 beta today. Until now I have experienced no erros, besides Amarok which won't play my songs.

This is what I get in the terminal, from when I load Amarok, to when I try playing a track.

kristoffer@kristoffer-laptop:~$ amarok
Object::connect: No such signal BrowserCategoryList::leavingTree()
Object::connect:  (sender name:   'internet')
Object::connect: No such signal BrowserCategoryList::leavingTree()
Object::connect:  (sender name:   'root list')
Object::connect: No such slot BrowserWidget::categoryChanged()
Object::connect:  (sender name:   'root list')
QLayout: Attempting to add QLayout "" to Playlist::SortWidget "", which already has a layout
QWidget::insertAction: Attempt to insert null action
Object::connect: No such signal BrowserWidget::widgetActivated( int )
Object::connect:  (receiver name: 'MainWindow')
Object::connect: No such signal CollectionWidget::home()
Object::connect:  (sender name:   'collections')
Object::connect:  (receiver name: 'root list')
Object::connect: No such signal ServiceBrowser::home()
Object::connect:  (sender name:   'internet')
Object::connect:  (receiver name: 'root list')
Object::connect: No such signal BrowserCategoryList::leavingTree()
Object::connect:  (sender name:   'playlists')
Object::connect: No such signal PlaylistBrowserNS::DynamicCategory::home()
Object::connect:  (receiver name: 'playlists')
"building tree with 7 leafs." 
QString :  QVariant(QString, "") 
QIcon :  QVariant(QIcon, ) 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QIcon :  QVariant(QIcon, ) 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QIcon :  QVariant(QIcon, ) 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QIcon :  QVariant(QIcon, ) 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QIcon :  QVariant(QIcon, ) 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QIcon :  QVariant(QIcon, ) 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QIcon :  QVariant(QIcon, ) 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
m_groupHash:  
(0, 1, 2, 3, 4, 5, 6) 
Object::connect: No such signal PlaylistBrowserNS::PlaylistCategory::home()
Object::connect:  (receiver name: 'playlists')
Object::connect: No such signal PlaylistBrowserNS::PodcastCategory::home()
Object::connect:  (receiver name: 'playlists')
Object::connect: No such signal PlaylistBrowserNS::PlaylistBrowser::home()
Object::connect:  (sender name:   'playlists')
Object::connect:  (receiver name: 'root list')
Object::connect: No such signal FileBrowser::Widget::home()
Object::connect:  (sender name:   'files')
Object::connect:  (receiver name: 'root list')
amarok:  ********************************************************************************************** 
amarok:  ** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: ** 
amarok:  ** amarok --debug                                                                           ** 
amarok:  ********************************************************************************************** 
kristoffer@kristoffer-laptop:~$ HTTP GET  QUrl( "http://post.audioscrobbler.com:80/?hs=true&p=1.2.1&c=ark&v=2.2.0&u=KriZo&t=1255809729&a=e7e69abc4a350d1b0c49e840b6e2fdc4&api_key=402d3ca8e9bc9d3cf9b85e1202944ca5&sk=a868b6ddad80448267f0ca01970b145c" )  
Object::connect: No such signal Playlist::GroupingProxy::activeRowChanged( int )
Object::connect:  (sender name:   'GroupingProxy')
Object::connect: No such signal Playlist::GroupingProxy::activeRowChanged( int )
Object::connect:  (sender name:   'GroupingProxy')
Object::connect: No such signal Playlist::GroupingProxy::activeRowChanged( int )
Object::connect:  (sender name:   'GroupingProxy')
"OK
3867bc54705741fd93a3d3ced008a62c
[http://post.audioscrobbler.com:80/np_1.2](http://post.audioscrobbler.com:80/np_1.2)
http://post2.audioscrobbler.com:80/protocol_1.2" 
QPainter::begin: Cannot paint on a null pixmap
QPainter::translate: Painter not active
QPainter::end: Painter not active, aborted
0 
HTTP POST:  QUrl( "http://post.audioscrobbler.com:80/np_1.2" )  "a=Autopilot%20Off&t=Make%20A%20Sound&b=Make%20A%20Sound&l=224&n=0&m=" 
HTTP POST:  QUrl( "http://post2.audioscrobbler.com:80/protocol_1.2" )  "a[0]=Autopilot%20Off&t[0]=Make%20A%20Sound&i[0]=1255809745&o[0]=P&r[0]=&l[0]=224&b[0]=Make%20A%20Sound&n[0]=0&m[0]=" 
"OK" 
"OK" 


I also get this [http://img188.imageshack.us/img188/4898/screenshotrg.png](http://img188.imageshack.us/img188/4898/screenshotrg.png)


Anyone knows how to solve this? In 9.04 I had a similar problem, which could be solved be removing the amarok folder in the .kde folder. But I doesn't help me this time.

---

### Post by fdmille on 2009-10-18
I'm getting pretty much the same set of errors, however I was able to get Amarok to play songs by following the instructions in the following thread:
[http://ubuntuforums.org/showthread.php?t=1137059&highlight=amarok](http://ubuntuforums.org/showthread.php?t=1137059&highlight=amarok)

---

### Post by KriZo on 2009-10-19
I got it working, but I didn't do anything, it just suddenly worked :S

---

