---
title: "Rhythmbox playlists and portable players"
date: 2013-01-08
forum: Multimedia Software
---

### Post by BBQdave on 2013-01-08
Ubuntu 12.04 Unity with [Rhythmbox]("https://live.gnome.org/Rhythmbox/FAQ") and [Sansa Clip+]("http://kb.sandisk.com/app/answers/detail/a_id/300") portable music player.

**How to use Rhythmbox playlists with Sansa Clip+**

_**1**_ Reformat and update Sansa Clip+
Set Sansa Clip+ *USB Mode* to **MSC**.

_**2**_ Mount and open Sansa Clip+ through Nautilus File Manager

Create a **.is_audio_player** file on the device. You can set a few fields  in this file to override the media-player-info device information like  this: 

[B]audio_folders=MUSIC/,RECORDINGS/
folder_depth=2
output_formats=application/ogg,audio/x-ms-wma,audio/mpeg[/B]

Unmount Sansa Clip+ from Nautilus File Manager

_**3**_ Open Sansa Clip+ with Rhytmbox - choose and sync playlists you want.

**Using Sansa Clip+** select *Music* > *Playlists* :D

---

