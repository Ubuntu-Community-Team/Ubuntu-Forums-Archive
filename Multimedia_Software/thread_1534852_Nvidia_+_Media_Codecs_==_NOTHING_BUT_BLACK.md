---
title: "Nvidia + Media Codecs == NOTHING BUT BLACK"
date: 2010-07-20
forum: Multimedia Software
---

### Post by Treth on 2010-07-20
I have Ubuntu Lucid 64-bit installed on a Core 2 Duo machine with an nVidia graphics card (Detailed specs if anybody thinks it would help!)

After installation, I activated the nvidia drivers, installed several codecs, and all that jazz we've come to expect when tuning a fresh install.  But whenever I try to play any media file whatsoever, I get nothing but a black window.  Maximized, normal size, gXine, mPlayer, VLC, Totem--nothing makes a difference!

I've launched several players in the terminal and viewed their output, and they recognize the presence of a video stream, its parameters, and claim to be decoding it correctly . . . yet all I get is sound.  Flash videos work fine in Firefox, so I can't pin this down.  This may be a duplicate, but I hope you can understand this is a notoriously vague problem to put into terms Google can understand.

Please help!  If any system specs or package versions would help, please ask and I'd be happy to provide whatever information you may need.

---

### Post by mc4man on 2010-07-20
Try a different video output, probably x11 is best to start, to test use cli, 
for mplayer 
 mplayer -vo x11 /path/to/filename, 
for vlc 
vlc --vout x11 /path/to/filename

> Detailed specs if anybody
certainly would be a good idea

(if it turns out to be that and you can't get Xv output then for mplayer and fs with x11 you'll need to add -zoom or try another -vo
(mplayer -vo help (gl2, sdl

Edit: plus which nvidia driver are you using?

---

### Post by Treth on 2010-07-22
Hardware manager says the nvidia driver version is 173.  I rolled it back from 'current' to see if I could get this to work right--I may upgrade again and then check the X11 output method.

And, yes, with the X11 display driver, it works!  I've begun poking through display output drivers in other players and it seems to be working there as well, though I can't spot the config options for totem.

Perhaps the most telling is that the Xine player using OpenGL works correctly, which suggests that the nvidia driver may not be entirely to blame but the XVideo extension may be the source of the problem.  Here's some relevant system bits:

01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)

Kernel:

2.6.32-23-generic

I suppose my problem is solved well enough, but I do worry about other problems down the line with Xv not doing its thing right.  Anybody think I should investigate further?

And also, thank you so much for your help!

---

### Post by mc4man on 2010-07-23
> though I can't spot the config options for totem.
For some "reason" ,the gui config for gstreamer A/V outputs is not enabled in the default menus

to get to 
```
gstreamer-properties
```

To enable in System -Preferences menu

R.click on Applications -> edit menus, you'll see a check box for 'Multimedia Systems Selector' in the Preferences menu

While you're there enable 'File Management', another useful disabled menu item.

---

