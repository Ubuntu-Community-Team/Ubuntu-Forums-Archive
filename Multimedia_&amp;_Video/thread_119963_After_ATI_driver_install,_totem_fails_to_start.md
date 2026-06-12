---
title: "After ATI driver install, totem fails to start"
date: 2006-01-20
forum: Multimedia &amp; Video
---

### Post by Noremacam on 2006-01-20
I installed the fglrx drivers using apt-get, following one of the guides on this forum, and now totem won't open. 

When I open it it says:
[QUOTE=Totem]
Totem could not startup.

The video output is in use by another application. Please close other video applications, or select another video output in the Multimedia Systems Selector.
[/QUOTE]

I know that to be false, because I just started the computer. In the Multimedia Systems Selector, it's set to XWindows (X11/XShm/Xv). When I press Test, it says:
> 
Failed to construct test pipeline for 'XWindows (X11/XShm/Xv)'

While the others work, they are slow, or limited. One for example, couldn't even stretch the video when I went to full screen. VLC won't play videos either.

Interestingly enough, Xine can play videos, with th Xv driver selected in the options(which doesn't make any sense to me).

I need totem and vlc to work. I'd hate to think I'd have to keep switching programs because they break like this.

Any help would be greatly appreciated. I'm not 100% the video failure is related to the ati driver, but the timing seems more than ironic to me.

---

### Post by Noremacam on 2006-01-23
Has anyone else had this problem? Is there an alternative renderer that I can use instead of Xv?

---

