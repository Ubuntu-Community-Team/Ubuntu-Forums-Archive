---
title: "Amarok 2.4 backport for Kubuntu 10.10 64bit playlist saving problems"
date: 2011-03-06
forum: Multimedia Software
---

### Post by ib80 on 2011-03-06
Hi,

I just updated amarok from 2.3.2 to the 2.4.0 version while still using Kubuntu 10.10 as I chose to use the backport repositories.

After the upgrade, I am no longer able to save my playlists to the disk using the button "Save current playlist" that is found in the bottom right corner of the user interface. The option to save the playlist on disk is there but does nothing.

Also, when I save the playlist using the Playlist -> Export Playlist As ... menu item, the title tag is not added to the playlist file when saving an xspf format. When amarok is restarted, the new playlist file is shown without a name.

I am using Kubuntu 10.10 64 bit edition.

Anyone having the same issues ? Any idea how to fix this ?

Here is some output using the debug mode of amarok :
```

amarok:               END__: void Context::AppletToolbar::appletAdded(Plasma::Applet*, int) [Took: 0.001s] 
amarok:             END__: void Context::VerticalAppletLayout::addApplet(Plasma::Applet*, int) [Took: 0.001s] 
amarok:           END__: virtual Plasma::Applet* Context::VerticalToolbarContainment::addApplet(const QString&, int) [Took: 0.079s] 
amarok:         END__: virtual void Context::VerticalToolbarContainment::loadConfig(const KConfigGroup&) [Took: 0.081s] 
amarok:       END__: void Context::ContextView::showHome() [Took: 0.082s] 
amarok:     END__: void ContextDock::createContextView(Plasma::Containment*) [Took: 0.13s] 
amarok:   END__: void Context::ContextScene::loadDefaultSetup() [Took: 0.14s] 
amarok: END__: virtual void ContextDock::polish() [Took: 0.2s] 
amarok: BEGIN: void Playlist::PrettyListView::slotPlaylistActiveTrackChanged() 
amarok:   BEGIN: void Playlist::PrettyListView::scrollToActiveTrack() 
amarok:   END__: void Playlist::PrettyListView::scrollToActiveTrack() [Took: 0.02s] 
amarok: END__: void Playlist::PrettyListView::slotPlaylistActiveTrackChanged() [Took: 0.02s] 
amarok: setting layout to QRectF(0,0 0x30) 
amarok: setting layout to QRectF(0,0 446x30) 
amarok: BEGIN: void RecentlyPlayedListWidget::setupTracksData() 
amarok: END__: void RecentlyPlayedListWidget::setupTracksData() [Took: 0.27s] 
amarok: BEGIN: void CurrentTrack::dataUpdated(const QString&, const QHash<QString, QVariant>&) 
amarok: END__: void CurrentTrack::dataUpdated(const QString&, const QHash<QString, QVariant>&) [Took: 0s] 
amarok: BEGIN: void ProgressWidget::redrawBookmarks(const QString*) 
amarok: END__: void ProgressWidget::redrawBookmarks(const QString*) [Took: 0s] 
amarok: BEGIN: void Playlist::Dock::slotSaveCurrentPlaylist() 
amarok:   BEGIN: virtual Playlists::PlaylistPtr Playlists::PlaylistFileProvider::save(const Meta::TrackList&, const QString&) 
**amarok:     [ERROR__] "Do not support filetype with extension "2011 18_27_49)!""** 
amarok:   END__: virtual Playlists::PlaylistPtr Playlists::PlaylistFileProvider::save(const Meta::TrackList&, const QString&) [Took: 0s] 
amarok: END__: void Playlist::Dock::slotSaveCurrentPlaylist() [Took: 0.002s] 
amarok: BEGIN: void SqlRegistry::emptyCache() 
amarok:   [SqlRegistry]   albums: 0 (-10) of 206 cached 
amarok:   [SqlRegistry]  artists: 0 (-10) of 212 cached 
amarok:   [SqlRegistry]   genres: 0 (-1) of 5 cached 
amarok:   [SqlRegistry]   tracks: 0 (-10) of 785 cached 
amarok: END__: void SqlRegistry::emptyCache() [Took: 0s] 
amarok: BEGIN: void SqlRegistry::emptyCache() 
amarok:   [SqlRegistry] Cache unchanged 
amarok: END__: void SqlRegistry::emptyCache() [Took: 0s] 
amarok: BEGIN: void SqlRegistry::emptyCache() 
amarok:   [SqlRegistry] Cache unchanged 
amarok: END__: void SqlRegistry::emptyCache() [Took: 0s] 

```

Regards

---

