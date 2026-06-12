---
title: "ATi + mplayer video tearing fix"
date: 2010-01-09
forum: Multimedia Software
---

### Post by MrDelish on 2010-01-09
I spent a good couple of hours trying to figure this out, so I figured I would post my results for reference.

I recently upgraded to Ubuntu Karmic and couldn't get any videos to play without tearing with my ATI Sapphire Radeon 3650 (proprietary drivers), even with compiz disabled. I also didn't like how the mouse cursor stayed on while videos were at full screen. After searching fruitlessly for fixes to these problems, I jumped into the #mplayer IRC channel and found out a couple interesting facts that I wish I'd known before:

- mplayer itself does not have a GUI by default
- The version of mplayer included in the repositories comes with a GUI (gmplayer), but it is not updated

I found two solutions that worked for me:

1) Use a custom command that would run my videos fine without a GUI (right-click a file -> Properties -> Open With -> Add -> Use Custom Command):

mplayer -vo gl2 -demuxer lavf -fs -framedrop

2) Install smplayer from the repository and switch the video output driver to "gl (fast - ATI cards)".

Hopefully this helps someone else that may be facing the same problem.

---

