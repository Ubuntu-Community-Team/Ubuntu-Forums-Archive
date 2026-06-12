---
title: "Using multiple displays"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by DannyW on 2007-04-14
Ok, I've installed the binary ati driver, fglrx. I have my TV set up as part of a big desktop (to the right).

The thing is, I'm not really sure how to use it...

I'm used to this in Windows where I can just move an application to the other screen by dragging it off to the right. The only thing I can move between the screens in Ubuntu, however, is the cursor.

Can anyone explain to me how this sort of setup is commonly used, or provide a link to an appropriate thread/guide (I've looked).

All I'm wanting to do is be able to simply play a video on the TV whilst leaving the primary monitor free to do other things - email, web browsing, etc. If there is a better way to achieve this, even if not utilising an extended desktop, please let me know, as this will be the TV's only function.

The only way I can play videos on the TV is by looking at it and opening Nautilus on the TV, then browsing to the video, and opening - This can be quite a pain, as small text is very difficult to read on my old TV.

Also, a separate issue: Once the video is playing on the TV the video is stretched vertically, but cropped so it appears the correct size, but I can only see the top half of the video. This only happens on the TV.



Any help would be greatly appreciated.

Thanks in advance,
Danny

---

### Post by wankel on 2007-04-14
Hi Danny W,

Did you have a look at the longer running thread on big desktops? 

[http://ubuntuforums.org/showthread.php?t=301941&page=10](http://ubuntuforums.org/showthread.php?t=301941&page=10)


Good luck with your setup!


(edit: pointed to the incorrect page in the thread)

---

### Post by DannyW on 2007-04-14
> **wankel said:**
> Hi Danny W,

Did you have a look at the longer running thread on big desktops? 

[http://ubuntuforums.org/showthread.php?t=301941&page=10](http://ubuntuforums.org/showthread.php?t=301941&page=10)


Good luck with your setup!


(edit: pointed to the incorrect page in the thread)
Ah, thank you very much, wankel, that's surely a thread for favourites.

I had to change the desktop mode to horizontal using 'sudo aticonfig --dtop=horizontal'.

This turned my desktop into the more familiar windows style big desktop - excellent, back to watching my programs ;)

However, I am still interested if anyone can explain the differences between dual-head (i.e. aticonfig --initial=dual-head) and horizontal (aticonfig --dtop=horizontal).

I will continue reading through that larger thread though, maybe the answer is in there somewhere.

EDIT: Unfortunately the video problem is still present.
> Also, a separate issue: Once the video is playing on the TV the video is stretched vertically, but cropped so it appears the correct size, but I can only see the top half of the video. This only happens on the TV.
I can drag the video player to the main display and all is suddenly fine, I move it to the TV and it becomes stretched and cropped.
EDIT2: This problem is with Totem, gxine and MPlayer - VLC is fine.

Advice?

---

