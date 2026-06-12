---
title: "Unable to change default app for AVI and FLV (tried everything!!)"
date: 2014-11-02
forum: Multimedia Software
---

### Post by The Bright Side on 2014-11-02
Hey guys,

okay, I'm going crazy with this one. I updated to Ubuntu GNOME 14.10 today and installed the following two media players: GNOME Media Player (an old program that allows to switch between playback engines) to play my 5.1 Surround music, and VLC Media Player to play my videos (it sucks playing back multichannel mixes in AC3, which is why I chose GNOME Media Player, which supports the GStreamer engine).

Now, I manually associated the multichannel file formats (FLAC, MKA, AC3 etc.) to GNOME Media Player, stereo audio files to Audacious, and videos to VLC. In the Ubuntu settings ("Details" app) I defined VLC as my main video player, too.

However, Ubuntu simply won't let me change the default app for AVI and FLV from GNOME Media Player to VLC!! Here's what I tried:

[LIST]
[*]Set VLC as default video player in "Details"
[*]Right-click on file, select Properties => Open With => select VLC, but GNOME Media Player **remains in the default spot** after I confirm!
[*]Try to change default application in Ubuntu Tweak. Same result: I make the change, confirm, and GNOME Media Player remains
[*]Edit defaults.list in **/etc/gnome** (in this file, all formats are associated with totem, nothing with VLC or GNOME Media Player, so I left it untouched)
[*]Edit defaults.list in **/usr/share/applications** (in this file, all formats are associated with totem, nothing with VLC or GNOME Media Player, so I left it untouched)
[*]Create defaults.list in **~/.local/share/applications** (file didn't exist, so I made it and manually put associations for VLC into it)
[*]Uninstall GNOME Media Player (VLC becomes default), then re-install GNOME Media Player (it becomes default and I'm back to square one)
[/LIST]

Folks, I'm at the end of my wits. Is there any way to crowbar this? I really do want VLC to open when I double-click on AVIs. :-(

---

