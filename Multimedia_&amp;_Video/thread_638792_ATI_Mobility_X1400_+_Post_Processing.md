---
title: "ATI Mobility X1400 + Post Processing"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by Cygoku on 2007-12-12
I get some strange video glitches when I play them on either VLC, Totem or MPlayer.  To best describe the glitches, it's like if the image was split in half horizontaly, as if each part gets unsynced.  My guess would be that there is no post processing.  

I am currently using a DELL Inspiron 6400, Ubuntu 7.10, ATI driver are latest 7.11.  

Please help! :)

Cygoku

---

### Post by Cygoku on 2007-12-13
*bump*

Sorry.

Cygoku

---

### Post by Cygoku on 2008-01-07
Yet another *bump*

---

### Post by sloggerkhan on 2008-01-07
You haven't explained your problem well enough for me to make head or tail of it.

---

### Post by entropic_existence on 2008-01-08
I think I'm having the same problem. And I had run into this problem before with different versions of Ubuntu and different ATI drivers. Inspiron 9400 here with the ATI x1400 video card. I have the newest ATI driver (8.443 Catalyst version 7.12) installed manually. (I much prefer the manual method over installing the older driver from the Ubuntu repo's. 

Initial configuration was done, Compiz is working with the 3D effects and all of that. Doesn't seem quite as smooth as my previous install which was Edgy Eft but that is neither here nor there.Ok so initial video overlay was Xv as recommended. Went to play an avi today in Mplayer and the video doesn't work properly. It plays but it flickers and jumps. I'll get a flickering horizontal line that flashes down across the video as it flickers, etc. Just generally bad video.

The install guide 5 went by at the cchtml wiki mentioned that if the Video overlay causes video problems try switching to disable or to OpenGL overlay. Tried both, same deal.

Now I haven't tried to see what happens if I watch a DVD, WMV or MPEG video since pretty much everything I have access to at the moment is avi. I did however try streaming video in a flash player on the web earlier today and it plays fine, no jumping or flickers.

---

### Post by entropic_existence on 2008-01-08
Ok looks like I may have found it, looks like it is an issue between the ATI drivers (hopefully will be fixed in the next release) and Compiz. The video will play fine in fullscreen unless another window is open and visible (contextual menus, etc). So these two threads:

[http://ubuntuforums.org/showthread.php?t=639203&highlight=x1400+video](http://ubuntuforums.org/showthread.php?t=639203&highlight=x1400+video)

[http://ubuntuforums.org/showpost.php?p=2892802&postcount=6](http://ubuntuforums.org/showpost.php?p=2892802&postcount=6)

Discuss it. Obviously turning Compiz off when playing a video will work. You can also change your video output mode to X11 instead of Xvid as discussed in the second link.

Hope that helps! It has worked for me.

---

