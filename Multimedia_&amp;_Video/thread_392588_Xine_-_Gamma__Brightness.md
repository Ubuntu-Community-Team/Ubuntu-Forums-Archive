---
title: "Xine - Gamma / Brightness"
date: 2007-03-24
forum: Multimedia &amp; Video
---

### Post by keithdw on 2007-03-24
I'm new to Linux and am having some trouble with the transition from WinXP, but I'm getting there and I'm happy with most things.

For video playback I've found Xine to be my player of choice, but I find the picture too dark (my general desktop experience is just right!). Anyway, the video controls in Xine don't seem to be available (brightness / contrast / hue etc) unless I select the OpenGL drivers. Using these drivers the picture quality is very much degraded, so this is not an option.

So, I use the 'Auto' drivers whatever they are end enjoy a great picture quality, but too dark.

This can be fixed by going to the Video Menu, Post Process, Chain Reaction and applying the eq2 filter with a gamma of about 1.25. Unfortunately, Xine does not remember this setting and I have to apply it each time I load the software.

Does anybody know how I can add this to the command line so that xine starts up with this set!!

Cheers

---

### Post by oliver69 on 2008-03-11
Hi keithdw!

Nearly one year has passed since you asked, but this may help other people too. With Google I saw many posts describing this problem - but no solution. So after some reading and testing I found this:

To choose post-plugins and parameters of chain-reaction there is a command line argument. Parameters are separated by "," and multiple post-plugins would be separated by ";".

> xine --post eq2:gamma=1.30,contrast=1.03 "dark_movie.avi"

According to the man-page xine reads additional arguments from "~/.xine/xinerc", one per line. But with complex arguments it is a bit...tricky (this took me quite a while :p). There has to be a newline at each space. So create this file with **two(!)** lines:

------  ~/.xine/xinerc  -------
--post
eq2:gamma=1.30,contrast=1.03
---------------------------------

And now enjoy a really dark movie! :D

---

### Post by Cresho on 2008-07-07
thanks a bunch!  I must of spent days trying to figure this out.

Here is my command incase someone wants a sharper image

--post
unsharp:Luma_amount=1.0

I also have a launcher command that launches it in full screen and no controls


xine -f -I dvd:// %u --post unsharp:Luma_amount=1.5 along with the top post in the xinerc to chain it.  It works!  I changed the eq2 saturation because my monitor has too much colors already

---

