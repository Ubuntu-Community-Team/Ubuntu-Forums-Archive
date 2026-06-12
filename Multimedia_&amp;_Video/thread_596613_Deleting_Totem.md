---
title: "Deleting Totem"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by mschraier on 2007-10-29
While playing around sith different DVD players my Totem stopped reading the video portion of the disc.  I have installed mplayer and it works fine.  My question is:

Under preferred applications>multimedia i used custom and input gmplayer. However Totem is still the default player.  How do I fix this?  If I want delete Totem I have to use Synaptic.  If I totally remove it and its associated files (gstreamer, xine, etc.) will this mess up MPlayer?  Bottom line, I want Mplayer to open when a DVD is inserted.

---

### Post by srhlefty on 2007-10-31
Synaptic should let you know if doing a complete removal will break MPlayer, since that's a dependency issue.  So I wouldn't worry about removing totem.  After all, even if Mplayer does break, you can always reinstall it as well.

I don't know the correct way to get Mplayer to run when you insert a disc.

---

### Post by perixx on 2007-10-31
Hi mschrainer...

have a look a my post here...

> [http://ubuntuforums.org/showthread.php?t=584700](http://ubuntuforums.org/showthread.php?t=584700)

Btw, if you haven't already installed gconf-editor, you can do so by opening a Terminal and entering:
> sudo apt-get install gconf-editor

I hope this helps ;)

Oh, and, I'd recommend to completely removing that trashy totem+plugin.


perixx

---

