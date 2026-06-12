---
title: "VLC client access playlist on network server"
date: 2008-12-24
forum: Multimedia Software
---

### Post by gkinal on 2008-12-24
The following works when using VLC under Windows and also under MacOS 10.5; it generates a series of error messages under Ubuntu 8.04.

On a computer that is networked (SMB/CIFS), I have some shared directories. These are visible to the other computers on the network. In these same directories, I have M3U format playlists, which in turn refer to a series MPEG2 .VOB files. These can be in the same (sub)directory or in different directories, and are referred to by their shared path names.

When it works (Mac, Windows), VLC reads the playlist and proceeds to process it by playing the series of MPEG2 files - think of it as video on demand over the network.

On the Ubuntu netbook machine, if I launch the same playlist, mplayer is brought up and works correctly (although it asks for access to the keychain - thus it wants a password for accessing the shared directory). If I start VLC and access the same playlist, the playlist is obviously seen, because I get an error window saying that the MPEG/VOB files cannot be accessed. 

I can understand that there may be a permissions problem, but if VLC can access the playlists, why can't it access the MPEG files which have the same permissions ?  (All shares are designated as usable by all users). Does VLC/Ubuntu "look" different to the host/server than VLC/MacOS ?

GK

---

