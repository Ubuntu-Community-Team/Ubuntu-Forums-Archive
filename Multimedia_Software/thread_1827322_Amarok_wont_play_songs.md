---
title: "Amarok wont play songs"
date: 2011-08-17
forum: Multimedia Software
---

### Post by u-noob-tu on 2011-08-17
im brand new to kubuntu and ived never used amarok before and its kinda confusing me. i have all my songs imported and they all show up, but they wont play. double clicking them doesnt do anything, though at the bottom right of the amarok window it says "now playing [song title]". ive gotten a few songs to play but not most of them.

---

### Post by fdrake on 2011-08-17
did you check if you have all your codecs installed? Make sure you check all your repositories and that you have gstreamer (latest version).
try playing with mplayer if that works

sudo apt-get install mplayer* gstreamer*

---

### Post by fdrake on 2011-08-17
if that doesn't work post here the output of the terminal

---

### Post by u-noob-tu on 2011-08-17
i ran amarok from the terminal and it says about TagLib and debugging mode. ```
ryan@ryan-Studio-1737:~$ amarok
KGlobal::locale::Warning your global KLocale is being recreated with a valid main component instead of a fake component, this usually means you tried to call i18n related functions before your main component was created. You should not do that since it most likely will not work 
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
QWidget::setMinimumSize: (Context dock/ContextDock) Negative sizes (0,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (0,-1) are not possible
amarok(10441)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/ryan/.config/ibus/bus
amarok(10441)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
amarok(10441)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
amarok(10441)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (0,-1) are not possible
QWidget::setMinimumSize: (Context dock/ContextDock) Negative sizes (0,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (90,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (90,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (90,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (90,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (309,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (309,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (309,-1) are not possible
********************************************************************************************** 
** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: ** 
** amarok --debug                                                                           ** 
**********************************************************************************************
```

Oh and i do have all gstreamer plugins installed.

---

### Post by fdrake on 2011-08-17
try to play a song:
> 
amarok "/home/ryan/Desktop/anySong.mp3"


you simply started the program it does not say much about your problem.
if you cannot play the file then post here the output.

---

### Post by u-noob-tu on 2011-08-18
tried playing from terminal, heres the code. ```
ryan@ryan-Studio-1737:~/Music/Oceana$ amarok Oceana - The Family Disease.m4a
KGlobal::locale::Warning your global KLocale is being recreated with a valid main component instead of a fake component, this usually means you tried to call i18n related functions before your main component was created. You should not do that since it most likely will not work 
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
QWidget::setMinimumSize: (Context dock/ContextDock) Negative sizes (0,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (0,-1) are not possible
amarok(11401)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/ryan/.config/ibus/bus
amarok(11401)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
amarok(11401)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
amarok(11401)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (0,-1) are not possible
QWidget::setMinimumSize: (Context dock/ContextDock) Negative sizes (0,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (90,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (90,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (90,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (90,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (309,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (309,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (309,-1) are not possible
matchString =  "^(itpc|pcast|feed)" 
found at  -1 
matchString =  "^(itpc|pcast|feed)" 
found at  -1 
matchString =  "^(itpc|pcast|feed)" 
found at  -1 
matchString =  "^(itpc|pcast|feed)" 
found at  -1 
matchString =  "^(itpc|pcast|feed)" 
found at  -1 
********************************************************************************************** 
** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: ** 
** amarok --debug                                                                           ** 
********************************************************************************************** 
ryan@ryan-Studio-1737:~/Music/Oceana$ amarok(11401) KWidgetItemDelegateEventListener::eventFilter: User of KWidgetItemDelegate should not delete widgets created by createItemWidgets! 
amarok(11401) KWidgetItemDelegateEventListener::eventFilter: User of KWidgetItemDelegate should not delete widgets created by createItemWidgets! 
amarok(11401) KWidgetItemDelegateEventListener::eventFilter: User of KWidgetItemDelegate should not delete widgets created by createItemWidgets! 
amarok(11401) KWidgetItemDelegateEventListener::eventFilter: User of KWidgetItemDelegate should not delete widgets created by createItemWidgets! 
amarok(11401) KWidgetItemDelegateEventListener::eventFilter: User of KWidgetItemDelegate should not delete widgets created by createItemWidgets! 
amarok(11401) KWidgetItemDelegateEventListener::eventFilter: User of KWidgetItemDelegate should not delete widgets created by createItemWidgets! 
amarok(11401) KWidgetItemDelegateEventListener::eventFilter: User of KWidgetItemDelegate should not delete widgets created by createItemWidgets! 
amarok(11401) KWidgetItemDelegateEventListener::eventFilter: User of KWidgetItemDelegate should not delete widgets created by createItemWidgets! 
amarok(11401) KWidgetItemDelegateEventListener::eventFilter: User of KWidgetItemDelegate should not delete widgets created by createItemWidgets! 
amarok(11401) KWidgetItemDelegateEventListener::eventFilter: User of KWidgetItemDelegate should not delete widgets created by createItemWidgets! 
amarok(11401) KWidgetItemDelegateEventListener::eventFilter: User of KWidgetItemDelegate should not delete widgets created by createItemWidgets! 
amarok(11401) KWidgetItemDelegateEventListener::eventFilter: User of KWidgetItemDelegate should not delete widgets created by createItemWidgets! 


```

---

### Post by .... on 2011-08-18
```
sudo apt-get install libxine1-all-plugins
```
As for being able to hear the songs, make sure your sound works correctly in system settings.

---

### Post by u-noob-tu on 2011-08-18
> **.... said:**
> ```
sudo apt-get install libxine1-all-plugins
```As for being able to hear the songs, make sure your sound works correctly in system settings.
still not working. strange, because at first it did work, just not with every song. now it wont play anything. my speakers are working, i tested everything in the system settings. and gstreamer is my audio backend, as well.

---

### Post by fdrake on 2011-08-19
> **u-noob-tu said:**
> still not working. strange, because at first it did work, just not with every song. now it wont play anything. my speakers are working, i tested everything in the system settings. and gstreamer is my audio backend, as well.

well it's not workin with xine so you better stick with gstreamer
```

sudo apt-get purge xine*
sudo apt-get install gstreamer

```
also try to play the song with mplayer
```

mplayer /path/of/your/song.m4a

```

---

### Post by u-noob-tu on 2011-08-20
i tried to remove xine, but it either wont uninstall it or it isnt installed. terminal output said it cannot remove virtual packages like xine. also, mplayer works fine, i just dont like it all that much.

---

