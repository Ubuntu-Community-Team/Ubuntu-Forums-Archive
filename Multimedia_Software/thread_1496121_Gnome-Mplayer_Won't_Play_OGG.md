---
title: "Gnome-Mplayer Won't Play OGG?"
date: 2010-05-28
forum: Multimedia Software
---

### Post by gerowen on 2010-05-28
I get this when I try to watch a screen-cast session I captured with gtk-recordmydesktop.  The same video plays fine in Totem, however Totem's browser embed blows, the only way I've been able to stream embedded videos is with the mplayer plugin, gecko-mediaplayer.  I found this out while trying to watch the ROV videos on BPs website.  Now normally I would just install the gecko-mediaplayer plugin and remove the Gnome-Mplayer GUI, and then install the Totem GUI and remove the totem-plugins.  However, Ubuntu won't let me do this, it's all or nothing.

Edit: Forgot to post the link, :p
**[Screenie](http://dl.dropbox.com/u/6017319/Screenshots/gnome-mplayer-ogg.png)**

---

### Post by gerowen on 2010-05-28
I think I know why, MPlayer supports ogg and ogm, but the video file I made is .ogv.  Weird that it doesn't support it.

---

### Post by WinterRain on 2010-05-28
You don't need to remove totem plugins to use gecko mediaplayer. Firefox can handle both.

---

