---
title: "How to configure firefox to play all multimedia with totem?"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by kaleman on 2007-03-25
Hi,

I replaced totem-gstreamer by totem-xine and now totem plays almost any media file. It even works very well in combination with beryl.

In firefox, I'm using the totem-mozilla plugin. However, firefox opens only a limited number of media types with totem. For example, if I try to open audio/x-ms-wma, firefox does not know that it should use totem to open it. If I open standalone totem and open the same audio/x-ms-wma, it plays perfectly. So, I just have to tell firefox to open audio/x-ms-wma files (among others) with totem.

Is there a way to do this?

The VLC plugin is not an alternative, since it only shows a "(no video)" message whenever it opens (whereas the standalone VLC works perfectly). I could use MPlayer as an alternative, but for a number of reasons I personally prefer totem.

In general, if you install more than one plugin that can handle the same format, it is a matter of chance which plugin firefox is going to choose. There should be a way to configure this.

Thanks a lot!

Michel

---

### Post by kaleman on 2007-03-26
I found the solution.

Asked the same question on [http://forums.mozillazine.org/viewtopic.php?p=2815245#2815245](http://forums.mozillazine.org/viewtopic.php?p=2815245#2815245).

The solution is to use the MediaPlayerConnectivity extension.

---

