---
title: "[SOLVED] VLC fullscreen issues on TV"
date: 2008-07-28
forum: Multimedia Software
---

### Post by Clappy on 2008-07-28
Howdy folks! I finally got sick of Windows and decided to install Ubuntu. This isn't my first foray into Linux (used to work as a webserver administrator) but my X/gnome/drivers/compiling skills are pretty lacking.

I have a Samsung display (primary) at 1600x1050 resolution, and a TV(svideo) at 1024x768. When I use VLC and fullscreen on the TV, it only displays the video in the top left corner, and the rest of the screen (and some of the samsung) is black. I think it's trying to use the Samsung's resolution when it fullscreens, is there ANY way to get it to use the TV's native resolution instead?

I am using an nvidia card Geforce 6800(I think?), and I am using twinview (not separateX). I would prefer not to use separate X because I want to be able to pick the videos from my Samsung, and drag the VLC player over. I can't see small text on the TV very well. Is there any kind of solution for an issue like this?

Thanks, let me know if you guys need any more information from me.

---

### Post by Clappy on 2008-07-29
I noticed another behaviour when I try to fullscreen on the TV. It does work for a split second and then shrinks into the upper left corner (using about 1/4 of the screen, the rest black)

I haven't been able to find a single other post here or elsewhere about this issue, and not for lack of trying. I have been searching for hours :popcorn:

---

### Post by ITAndrew on 2008-07-29
I would point you to [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

Also, I have tried to do this as well and have had nothing but problems. Have you tried to use any other media player (mplayer, gxine, or totem)?

My end solution was to use mythTV as a seperate X for playback, which looks as if its not the way you want to go.

Another solution that I can think of is desktop cloning, although you would most likely need to set your display all around to 1024x768 which is a PAIN if this is not a designated media box.

---

### Post by Clappy on 2008-07-30
Thanks for replying. Well, I wanted to use VLC because it's what I used on windows and I quite like it. Here's something else I figured out.

If I change the value of this line in my ~/.vlc/vlcrc from 0 to 1 (1 is my TV device ID):

# Fullscreen video output (boolean)
fullscreen=1

When I open something in VLC it will now open in fullscreen, on the TV, and use ALL of the screen, but if I try go back to windowed mode and back into fullscreen, it's the same problem!

So it will work for a split second when going from windowed mode, or it will work by changing that value in vlcrc but it doesn't stick if you change from fullscreen to windowed and back again.

Strange behaviour, I don't have the know-how to be able to fix this :(

---

### Post by Clappy on 2008-08-05
Well, I solved it by using X11 under preferences, video output in VLC.

---

