---
title: "Force videos to open in VLC"
date: 2013-04-30
forum: Multimedia Software
---

### Post by c-m on 2013-04-30
I can't seem to force videos to launch in VLC the crap movie player keeps loading instead. 

Sure I can select open with and VLC, but next time I click on the video it opens in the default player.

I'm running 13.04 and there's not 'set as default' option.

---

### Post by mc4man on 2013-04-30
As in the past you can right click on an example of a filetype > properties > open with & set vlc to be the default for that filetype.

What  has changed is now the  default video & or default audio player setting will set chosen player for all mimetypes that are supported (in the past it only set for 1 mimetype

To try out > System Settings > Details > Default Applications > Video > pick Vlc media player. 
After doing so,  to see changes, open this file 
```
gedit ~/.local/share/applications/mimeapps.list
```

---

### Post by c-m on 2013-04-30
Works, thanks.

---

