---
title: "How to play WMV media file?"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by chinese_ys on 2007-08-26
I downloaded some tutorial videos which have .wmv extension. When I use totem-gstreamer or totem-xine to play them, I got some codec error (See in the attached figures).

Anyone knows how to fix this? I am using Ubuntu 7.04 and I have installed media codecs using AUTOMATIX. 

Any valuable suggestion will be appreciated!

---

### Post by Majorix on 2007-08-26
I would suggest adding the Medibuntu repos (don't have the link but they come up as first on google) and then installing the w32codecs package.

---

### Post by Gremlinzzz on 2007-08-26
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by chinese_ys on 2007-08-26
I have updated my sources.list with the medibuntu source and reinstall codecs, but errors are still there.

---

### Post by Gremlinzzz on 2007-08-26
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)

---

### Post by Gremlinzzz on 2007-08-26
I play that format with smplayer and i reformatted flv to wmv with vlc player
so they both play wmv.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#VLC_plug-in_.28Installs_VLC_media_player_as_well.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#VLC_plug-in_.28Installs_VLC_media_player_as_well.29)
[http://smplayer.sourceforge.net/en/linux/index.php](http://smplayer.sourceforge.net/en/linux/index.php)

---

### Post by chinese_ys on 2007-08-27
> **Gremlinzzz said:**
> I play that format with smplayer and i reformatted flv to wmv with vlc player
so they both play wmv.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#VLC_plug-in_.28Installs_VLC_media_player_as_well.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#VLC_plug-in_.28Installs_VLC_media_player_as_well.29)
[http://smplayer.sourceforge.net/en/linux/index.php](http://smplayer.sourceforge.net/en/linux/index.php)

Thanks man! The smplayer works!

---

