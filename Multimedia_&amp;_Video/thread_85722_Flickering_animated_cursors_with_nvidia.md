---
title: "Flickering animated cursors with nvidia"
date: 2005-11-03
forum: Multimedia &amp; Video
---

### Post by mannheim on 2005-11-03
I recently installed an nvidia card in my Breezy machine (a GeForce 6200-based card). The card works fine, but since installing it, the animated cursors now flicker.

For example, if I launch Firefox from the panel, then the turning "wheel" cursor flickers unpleasantly during the few seconds it takes for Firefox to launch.

There was a very similar post [here]("http://ubuntuforums.org/archive/index.php/t-20243.html"), in the now-closed Hoary development forum, without any resolution. (I switched to nvidia because of unresolvable lockups that sometimes occured with my ATI card.) I am using the "nvidia" driver from the repositories, and an LCD monitor with the usual 60hz refresh rate.

Is there anything I can try here, to get back the polished look-and-feel that the cursor used to have?

---

### Post by 23meg on 2005-11-03
I have the same problem with my Geforce Go6200 chip. I've had it ever since I've started testing Breezy, but after doing a fresh install of the final release it started to happen less often; it's still there though, and is annoying.

---

### Post by mannheim on 2005-11-03
Well, maybe I found a workaround that works in my case at least: I just tried adding the line
```
Option 		"SWCursor" "True"
```
to the "Device" section of my xorg.conf; and it seems that this software-cursor option has got rid of the flickering. (Of course, maybe some other random event is the real cause! But I'm happy for now.)

Does anybody reading this know if there is any disadvantage to watch out for with SWcursor? I know nothing about it, but I naively assume that it just asks the CPU to do a tiny bit of work which could otherwise be done by the GPU.

---

### Post by mannheim on 2005-11-03
Replying again to my own post: I found at least one of the disadvantages of the software cursor. If I open up glxgears and move the cursor across the window, then the cursor disappears while it is over the glxgears window. Also, when playing a video (e.g. in totem player), if I move the cursor over the video, then there is a rectangle surrounding the moving cursor in which the video becomes blocky and slightly corrupted.

---

### Post by 23meg on 2005-11-04
I've tried the SWCursor trick and the flickering continues here.

---

### Post by mannheim on 2005-11-04
[QUOTE=23meg]I've tried the SWCursor trick and the flickering continues here.[/QUOTE]

That's interesting: I went back to HWCursor, and the flicker came back, so it wasn't an accident in my case. I guess we have different problems.

I found a thread on this flickering cursor [here.]("http://www.nvnews.net/vbulletin/archive/index.php/t-18872.html") The posters in that thread also had mixed experiences with SWCursor: it worked for some, and there did not seem to be a consensus about where to look for the cause.

---

