---
title: "smplayer gets stuck when mkv file is played.."
date: 2010-07-01
forum: Multimedia Software
---

### Post by CorruptDNA on 2010-07-01
i dont know what has happened but my smplayer gets stuck when i play any kind of mkv file.. it was working file til yesterday, and today, i had to restart my computer manually 10-15 times! 
heres the log for smplayer :

 p, li { white-space: pre-wrap; }  [02:29:48] main: lock_file: /home/umair/.smplayer/smplayer_init.lock
 [02:29:48] global_init
 [02:29:48] global_init: config file: '/home/umair/.smplayer/smplayer.ini'
 [02:29:48] Preferences::load
 [02:29:48] Translator::loadCatalog: can't load qt_en_US from /usr/share/smplayer/translations
 [02:29:48] Translator::loadCatalog: can't load qt_en_US from /usr/share/qt4/translations
 [02:29:48] Translator::loadCatalog: successfully loaded smplayer_en_US from /usr/share/smplayer/translations
 [02:29:48] This is SMPlayer v. 0.6.1 (SVN r1304) running on Linux
 [02:29:48] Qt v. 4.4.0
 [02:29:48]  * application path: '/usr/bin'
 [02:29:48]  * data path: '/usr/share/smplayer'
 [02:29:48]  * translation path: '/usr/share/smplayer/translations'
 [02:29:48]  * doc path: '/usr/share/doc/packages/smplayer'
 [02:29:48]  * themes path: '/usr/share/smplayer/themes'
 [02:29:48]  * shortcuts path: '/usr/share/smplayer/shortcuts'
 [02:29:48]  * smplayer home path: '/home/umair/.smplayer'
 [02:29:48]  * ini path: '/home/umair/.smplayer'
 [02:29:48]  * current path: '/home/umair'
 [02:29:48] SMPlayer::processArgs: arguments: 1
 [02:29:48] SMPlayer::processArgs: 0 = smplayer
 [02:29:48] SMPlayer::processArgs: files_to_play: count: 0
 [02:29:48] Recents::load
 [02:29:49] Core::Core: file_settings: '/home/umair/.smplayer/smplayer_files.ini'
 [02:29:49] MplayerProcess::init_rx
 [02:29:49] MplayerLayer::allowClearingBackground: 0
 [02:29:49] Preferences::monitor_aspect_double
 [02:29:49]  warning: monitor_aspect couldn't be parsed!
 [02:29:49]  monitor_aspect set to 0
 [02:29:50] Playlist::setModified: 0
 [02:29:50] Playlist::loadSettings
 [02:29:50] Playlist::addItem: '/home/umair/Desktop/[HorribleSubs] Naruto Shippuuden - 167 [480p].mkv'
 [02:29:50] Playlist::setModified: 0
 [02:29:50] name: '[HorribleSubs] Naruto Shippuuden - 167 [480p].mkv'
 WARNING: [02:29:50] QTableWidget: cannot insert an item that is already owned by another QTableWidget
 WARNING: [02:29:50] QTableWidget: cannot insert an item that is already owned by another QTableWidget
 [02:29:50] Style name: 'cleanlooks'
 [02:29:50] Style class name: 'QCleanlooksStyle'
 [02:29:51] BaseGui::initializeMenus
 [02:29:51] BaseGui::initializeMenus
 [02:29:51] BaseGui::updateRecents
 [02:29:51] BaseGui::updateWidgets
 [02:29:51] BaseGui::updateWidgets
 [02:29:51] BaseGui::updateRecents
 [02:29:51] PlaylistDock::hideEvent: isFloating: 0
 [02:29:51]  undocked
 [02:29:51] BaseGui::initializeMenus
 [02:29:51] BaseGui::updateRecents
 [02:29:51] BaseGui::updateWidgets
 [02:29:51] BaseGuiPlus::loadConfig
 [02:29:51] DefaultGui::createStatusBar
 [02:29:51] DefaultGui::createActions
 [02:29:51] DefaultGui::createControlWidget
 [02:29:51] TimeSlider::setDragDelay: 100
 [02:29:51] DefaultGui::createControlWidgetMini
 [02:29:51] TimeSlider::setDragDelay: 100
 [02:29:51] TimeSlider::setDragDelay: 100
 [02:29:51] BaseGui::initializeMenus
 [02:29:51] BaseGui::updateRecents
 [02:29:51] DefaultGui::updateWidgets
 [02:29:51] BaseGui::updateWidgets
 [02:29:51] DefaultGui::loadConfig
 [02:29:51] DefaultGui::updateWidgets
 [02:29:51] BaseGui::updateWidgets
 [02:29:51] SMPlayer::gui: changed working directory to app path
 [02:29:51] SMPlayer::gui: current directory: /usr/bin
 [02:29:51] BaseGui::showEvent
 [02:29:51] main: remove_lock: /home/umair/.smplayer/smplayer_init.lock
 [02:29:51] BaseGui::loadActions
 [02:29:51] ActionsEditor::loadFromConfig
 [02:29:52] BaseGui::initializeMenus
 [02:29:52] BaseGui::updateRecents
 [02:29:52] DefaultGui::updateWidgets
 [02:29:52] BaseGui::updateWidgets
 [02:29:56] BaseGui::showMplayerLog
 [02:30:06] BaseGui::showLog
 



if you know anything to help, like reinstalling or removing a package, id be grateful.. 
Thakns..

---

### Post by rvm4000 on 2010-07-02
> **CorruptDNA said:**
> 
 [02:29:48] This is SMPlayer v. 0.6.1 (SVN r1304) running on Linux


That version is very old. Why don't you update it to 0.6.9?

[http://smplayer.berlios.de/downloads.php](http://smplayer.berlios.de/downloads.php)

---

### Post by CorruptDNA on 2010-07-03
well i would but i dont think it would help, since i cant play mkv files in vlc either (even the ones that used to work, hang the computer. ) and can only  avi files ..

---

