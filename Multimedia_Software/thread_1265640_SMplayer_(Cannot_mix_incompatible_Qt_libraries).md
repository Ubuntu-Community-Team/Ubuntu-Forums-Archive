---
title: "SMplayer (Cannot mix incompatible Qt libraries)"
date: 2009-09-13
forum: Multimedia Software
---

### Post by r11_kaede on 2009-09-13
Hi guys,

I'm currently using Hardy Heron, 2.6.24-29, on HP Mininote 2133.

Previously my SMplayer used to work fine, with no problems whatsoever. But from a couple of days ago, my SMplayer would fail to load every single time.

When I tried to run it from terminal, this is what I got.

---
main: app name: smplayer
global_init
global_init: config file: '/home/profile/.smplayer/smplayer.ini'
Preferences::load
Debug: Translator::loadCatalog: can't load qt_en_US from /usr/share/smplayer/translations
Debug: Translator::loadCatalog: can't load qt_en_US from /usr/share/qt4/translations
Debug: Translator::loadCatalog: successfully loaded smplayer_en_US from /usr/share/smplayer/translations
This is SMPlayer v. 0.6.0rc2 (SVN 834) running on Linux
Debug: This is SMPlayer v. 0.6.0rc2 (SVN 834) running on Linux
Debug: Qt v. 4.3.3
Debug:  * application path: '/usr/bin'
Debug:  * data path: '/usr/share/smplayer'
Debug:  * translation path: '/usr/share/smplayer/translations'
Debug:  * doc path: '/usr/share/doc/packages/smplayer'
Debug:  * themes path: '/usr/share/smplayer/themes'
Debug:  * shortcuts path: '/usr/share/smplayer/shortcuts'
Debug:  * smplayer home path: '/home/profile/.smplayer'
Debug:  * ini path: '/home/profile/.smplayer'
Debug:  * current path: '/home/profile'
Debug: main: files_to_play: count: 0
Debug: main: changed working directory to app path
Debug: main: current directory: /usr/bin
Debug: Recents::load
Debug: Core::Core: file_settings: '/home/profile/.smplayer/smplayer_files.ini'
Debug: MplayerProcess::init_rx
Debug: MplayerLayer::allowClearingBackground: 0
Debug: Preferences::monitor_aspect_double
Debug:  warning: monitor_aspect couldn't be parsed!
Debug:  monitor_aspect set to 0
Debug: Playlist::setModified: 0
Debug: Playlist::loadSettings
Debug: Playlist::setModified: 0
Debug: Style name: 'cleanlooks'
Debug: Style class name: 'QCleanlooksStyle'
Debug: BaseGui::initializeMenus
Debug: BaseGui::initializeMenus
Debug: BaseGui::updateRecents
Debug: BaseGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: BaseGui::updateRecents
Fatal: Cannot mix incompatible Qt libraries
Aborted
---

Any help here would be much appreciated.

Thanks. :)

---

