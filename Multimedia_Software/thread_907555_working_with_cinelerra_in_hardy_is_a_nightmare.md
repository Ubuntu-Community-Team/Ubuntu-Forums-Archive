---
title: "working with cinelerra in hardy is a nightmare"
date: 2008-09-01
forum: Multimedia Software
---

### Post by mateuszbaranski on 2008-09-01
Hallo,
I am stuck with the cinlerra on hardy heron. I've been using cinelerra fo a long time on 6.10 and 7.04, 7.10. There were some minor bugs but it worked quite stable in 7.10. I switched to 8.04 and my life became a nightmare.

I tried to:
1) runing by root
2) changing kernels,
3) switching off the compiz,
4) installing XFCE instead of gnome,
5) use cinelerra version 4
6) deleting ~/.bcast
7) ....
And still nothing.
I spend hours trying to get it work. I managed to run cinelerra and even work but it is horrible while every 2 minutes I have to kill cinelerra and start it again. 

For users like me my hints (for not going crazy with the editing):
1) if nothing responds to clicks try to drag some resource in a track and then ctrl-z (undo) - it sometimes unlocks cinelerra
2) try to zoom in and zoom out (using ctrl and scroll on the mouse)
3) if you cannot arm or dissarm the track - try to use TAB from keyboard (mouse has to be abowe the control box of the track). Also try to use other keyboard shortcuts.
4) do not use IN and OUT points - If you do, it is sometimes impossible to scroll the timeline.

Did anyone try to compile cinelerra by himself? Maybe this helps?

EDIT: After some months not using cinelerra, there was an update of  kernel to 2.6.24.21-rt - it's much better.
Another thing is that I changed /etc/security/limits.conf and gave video group the real time prioroty:
@video          -       rtprio          90
@video          -       nice            -10

---

### Post by mateuszbaranski on 2008-12-22
Just for making some feedback: After several months at current stage of Cinelerra and kernel development I admit - it is much better. 

I can work even couple of hours in cinelerra without crash. 
Currently I use Cinelerra 2.1 CV and latest real-time kernel for ubuntu 8.04 (2.6.24-22-rt).

Still I cannot use IN and OUT  points (for cutting and pasting). When I put some IN point to the timeline - widgets stop responding (clicking on them does nothing).

---

