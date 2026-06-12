---
title: "XBMC, no window frame in windowed mode (KDE)"
date: 2013-09-21
forum: Multimedia Software
---

### Post by NHerby on 2013-09-21
Hi,
I have a very annoying issue with XBMC:
When I switch to windowed mode, the frame around XBMC window does not  appear anymore so I cannot resize or move the window. The app also does not appear in the taskbar and, even if  I select the XBMC window, I cannot use the keyboard. So I cannot come back  to fullscreen using the "toggle fullscreen" key. The only way to come  back to fullscreen is to stop the video to go in the  settings->system->video and switch to fullscreen.
I run XBMC on an external TV screen (not on my main monitor) using the nvidia separate x screen configuration.

I ran some software update recently but I'm not sure if this is the  cause of the problem. But before, I did not have this problem and I was able to switch from windowed to  fullscreen mode without issue.

Thanks for help.

---

### Post by NHerby on 2013-09-22
Well, thanks to the french Ubuntu forum, I found the solution:
The origin of this problem is the window manager that is not active anymore (don't ask why) on the second screen.
The magic command to fire it up is```
DISPLAY=:0.1 kwin
```
To start XBMC at the same time:```
DISPLAY=:0.1 kwin & DISPLAY=:0.1 xbmc 
```

---

