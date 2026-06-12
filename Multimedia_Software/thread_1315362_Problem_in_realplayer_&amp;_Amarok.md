---
title: "Problem in realplayer &amp; Amarok"
date: 2009-11-05
forum: Multimedia Software
---

### Post by skvaditya on 2009-11-05
Hi
I am using Ubuntu 9.10,gnome desktop & am facing problem in using real player & amarok. I removed & reinstalled both of them but the problem still persists. While typing amarok in terminal I get the following error.

-----------------------------------------------------------------------------------------------------
> aditya@aditya-desktop:~$ amarok
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
"building tree with 0 leafs." 
m_groupHash:  
() 
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
Object::connect: No such signal Playlist::GroupingProxy::activeRowChanged( int )
Object::connect:  (sender name:   'GroupingProxy')
Object::connect: No such signal Playlist::GroupingProxy::activeRowChanged( int )
Object::connect:  (sender name:   'GroupingProxy')
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x4c00024
amarok:  ********************************************************************************************** 
amarok:  ** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: ** 
amarok:  ** amarok --debug                                                                           ** 
amarok:  ********************************************************************************************** 
aditya@aditya-desktop:~$ Object::connect: No such signal Playlist::GroupingProxy::activeRowChanged( int )
Object::connect:  (sender name:   'GroupingProxy')
Object::disconnect: Unexpected null parameter
Object::disconnect: Unexpected null parameter
Object::disconnect: Unexpected null parameter
QCoreApplication::postEvent: Unexpected null receiver----------------------------------------------------------------------------------------------------
And for real player I get the following error.

-------------------------------------------------------------------------------------------------
> ** (realplay.bin:3160): WARNING **: Couldn't find pixmap file: track.png

** (realplay.bin:3160): WARNING **: Couldn't find pixmap file: nonsuperb.png

** (realplay.bin:3160): WARNING **: Couldn't find pixmap file: superbuffer.png

** (realplay.bin:3160): WARNING **: Couldn't find pixmap file: superbufferlive.png

** (realplay.bin:3160): CRITICAL **: file superbufhscale.cpp: line 493 (void hx_superbuf_hscale_init(HXSuperbufHScale*)): assertion `superbuf_hscale->tile_graphics[HX_SUPERB_MODE_BG].pixbuf' failed

(realplay.bin:3160): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:3160): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed--------------------------------------------------------------------------------------------------
As I am new to linux I am not able to understand what the problem is. Please help to resolve this.

Thnx in Advance
Adi

---

