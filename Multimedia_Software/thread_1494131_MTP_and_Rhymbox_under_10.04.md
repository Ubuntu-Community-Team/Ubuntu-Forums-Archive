---
title: "MTP and Rhymbox under 10.04"
date: 2010-05-26
forum: Multimedia Software
---

### Post by xian67 on 2010-05-26
Hi,
I own a Sony NWZ-E345 MP3 player that used to be seen by Rhythmbox when running 9.10 with no issues,  After enabling the plugin for MTP within Rythmbox the player was seen at connection.  However, after updating to 10.04 my MP3 player is not seen at all, even though MTP support is enabled under plugins.  As a matter of fact none of the media players I installed can see my player and they all support MTP.  I tried some other players as a troubleshooting step. I have confirmed that libmtp8 is installed via the repository. Has anyone encountered this as well? I suspect this may be an easy reply for someone.  BTW, this occurs with two different machines and nothing has changed with my MP3 player.  Thanks for the help.

---

### Post by RicGag on 2010-08-03
i'm also experiencing problems with my NWZ-E345 but only with playlists.

To have Rhythmbox handle the player, i have created the file .is_audio_player

in the root of the player with the following content:

audio_folders=MUSIC/
playlist_path=Playlists/
playlist_format=audio/x-iriver-pla
access_method.protocols=mtp
access_method.drivers=libmtp
output_formats=application/ogg,audio/x-ms-wma,audio/aac,audio/x-wav,audio/mpeg

Hope it works for you...

---

