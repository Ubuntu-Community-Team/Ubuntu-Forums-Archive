---
title: "Breezy Badger 5.10, ATI fglrx 8.18.8 , Xvideo support"
date: 2005-11-13
forum: Multimedia &amp; Video
---

### Post by vicomte on 2005-11-13
Breezy Badger 5.10,
ATI fglrx 8.18.8,
Xvideo support , i.e. none

I am trying to run mplayer from [http://www.mplayerhq.hu](http://www.mplayerhq.hu), which I downloaded and compiled via CVS. I have everything working including the gui. I have my ubuntu almost a totally clean install followed by ATI drivers installed with no problems following one of the plethora of how to's on this forum, but though everything else works I get this;

> 
==========================================================================
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
==========================================================================


-vo x11, -vo sdl, -vo gl, -vo gl2, all work fine, but I prefer Xvideo as many of the other video out styles carry no ability to scale the video size as Xvideo does. Though I may rescale the size of the window under xorg, the size of the video stays the same albeit centred in the video window.

I am looking for suggestions.

---

