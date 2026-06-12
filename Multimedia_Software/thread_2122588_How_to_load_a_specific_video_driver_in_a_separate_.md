---
title: "How to load a specific video driver in a separate X server?"
date: 2013-03-05
forum: Multimedia Software
---

### Post by figure002 on 2013-03-05
I configured my Ubuntu system (12.10, 64bit) so that I'm able to start any application in a separate X server. Running games or for example XBMC in a separate X server has some major advantages. I can run an application in a separate X server as follows:

```
xinit /usr/bin/xbmc -- :1
```

I already managed to [get sound working]("http://askubuntu.com/questions/147547/how-to-get-sound-in-a-separate-x-server-in-ubuntu-11-04-or-later") in the separate X server. The problem I'm having now is that when I'm in the separate X server, Ubuntu seems to load the wrong video driver. When, for example, I load XBMC in the main X server all works fine. But when I execute it in a separate X server, the graphics look ugly and are very slow too.

This happens on my laptop with an Intel HD Graphics 3000 chip (default driver). This problem does not occur on a different laptop with Ubuntu 12.10, an Nvidia GeForce G105M chip, and the proprietary Nvidia or nouveau driver.

I suspect that the wrong video driver is being loaded for the separate X server. I did get some clues from the command line. The command below was executed from the second X server:

```
serrano@saibot:~$ LIBGL_DEBUG=verbose xbmc
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
libGL error: failed to open drm device: Permission denied
libGL error: failed to load driver: i965
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/serrano/.drirc: No such file or directory.
Running DIL (3.22.0) Version
DtsDeviceOpen: Opening HW in mode 0
DtsDeviceOpen: Create File Failed
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
libGL error: failed to open drm device: Permission denied
libGL error: failed to load driver: i965
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/serrano/.drirc: No such file or directory.
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
libGL error: failed to open drm device: Permission denied
libGL error: failed to load driver: i965
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/serrano/.drirc: No such file or directory.
```

I don't really know where to go from here. Help is much appreciated.

---

### Post by figure002 on 2013-03-05
It wasn't until after I posed the above log that I noticed the "Permission denied" messages. This usually means insufficient privileges, so I did the following:
```
xinit -- :1
```
Then in the second X server:
```
sudo xbmc
```

And guess what, the graphics look as they should. I'm still confused why I'm getting these "Permission denied" messages. Could someone tell me how I can fix this? Having to execute regular programs as root is obviously not the right solution.

**EDIT:**

As a side effect of using 'sudo' in the above command sound no longer works properly in XBMC. Audio works until audio or a video is played. So this isn't a solution.

---

### Post by figure002 on 2013-03-27
I found the solution to my problem on this blog post: [https://kparal.wordpress.com/2013/02/17/how-to-run-graphical-applications-with-sudo/](https://kparal.wordpress.com/2013/02/17/how-to-run-graphical-applications-with-sudo/)

To keep it short, I had to add myself to the 'video' group: sudo usermod -a -G video $USER
Which is similar to the way I enabled audio in separate X servers: sudo usermod -a -G audio $USER

---

