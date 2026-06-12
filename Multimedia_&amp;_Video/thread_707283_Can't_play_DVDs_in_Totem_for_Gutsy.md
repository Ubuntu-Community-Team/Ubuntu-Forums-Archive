---
title: "Can't play DVDs in Totem for Gutsy"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by TE7 on 2008-02-25
I've tried all the suggestions in the forums. Installed the medibuntu repository. No help. Tried ito install vlc and totem-xine, but both faild with error messages for dependencies. When loadind the DVD while zine is open, it says some gstreamer plugins are missing. I've installed all gstreamers in Synaptic, but no help.

Thanks in advance for any help.

---

### Post by Melcar on 2008-02-25
Just get VLC.  I could never play DVDs with Totem either; it will always complain about missing codecs, and when it did play them, there was only sound.

---

### Post by TE7 on 2008-02-25
When I go to synaptic to mark vlc for install, it says there are dependencis which can't be installed: a few libraries and vlc-plugin-nox, which it says can't be installed. Is there another way to install VLC? ...with the dependent librairies?

---

### Post by TE7 on 2008-02-25
How about Kaffeine?

---

### Post by Melcar on 2008-02-25
Kaffeine uses Xine as default, and Xine is much better at playing DVDs (it supports menus too).  You could also use Xine instead of Gstreamer for Totem and it ill give you the same result (uninstall totem-gstreamer thought).  As for VLC, you sure you have all the Universe and Multiverse repositories on?  Maybe try the [Medibuntu]("http://www.medibuntu.org/") repositories?  Remember to always reload your package list when adding repositories.  Mplayer is another alternative, although the DVD menu navigation with it can be a bit clunky.

---

### Post by TE7 on 2008-02-25
Used the following forum post to install VLC, and it worked great.

[http://ubuntuforums.org/showthread.php?t=704726&highlight=VLC+gutsy](http://ubuntuforums.org/showthread.php?t=704726&highlight=VLC+gutsy)

---

