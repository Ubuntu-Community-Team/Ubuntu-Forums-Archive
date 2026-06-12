---
title: "Transparent Video on Workspace"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by K7522 on 2008-02-08
I have only recently made the move to Ubuntu on my main desktop, hello!

I used to have a program on 'dows that would play video at a set opacity overlayed on the desktop so that I could watch a movie while I surf the net, play games or whatever without sacrificing full screen video. The video would be undisturbed by mouse clicks and keypresses as it was only a watermark above the desktop, not an 'always on top' window.

Is there a way to accomplish this in Ubuntu? I've done some research and come up with absolutely nothing. Thanks in advance for your replies and time!

---

### Post by K7522 on 2008-02-09
Shameless bumpity?

---

### Post by K7522 on 2008-02-09
One more; has anyone seen this kind of program?

---

### Post by overdrank on 2008-02-09
> **K7522 said:**
> One more; has anyone seen this kind of program?

HI and you can use xwinwrap and you can download it here
[http://3v1n0.tuxfamily.org/apt-repository/dists/edgy/beryl-svn/](http://3v1n0.tuxfamily.org/apt-repository/dists/edgy/beryl-svn/)
and the code is here
[http://swik.net/xwinwrap](http://swik.net/xwinwrap)
and this thread may help
[http://ubuntuforums.org/showthread.php?t=577144](http://ubuntuforums.org/showthread.php?t=577144)
Good luck!

---

### Post by K7522 on 2008-02-10
Many thanks! You have saved me from the dreaded multitasking with a big video taking half of my screen.

For those interested in watermarking the video over everything as I did, I had to modify the command a bit after installation, as follows. Had to remove -st (skip taskbar) so that the program shows up on the task bar as "Untitled window" where you can right click it and set always on top.

xwinwrap -ni -o 0.4 -fs -s -nf -sp -- mplayer -wid WID -quiet '/MEDIA FILE'

Thanks again overdrank.

---

