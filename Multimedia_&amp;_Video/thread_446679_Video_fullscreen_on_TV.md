---
title: "Video fullscreen on TV"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by The_Fallen on 2007-05-17
Hi,

I am very frequently using the TV out of my Nvidia GF7600GT for watching movies on my TV. In Windows XP for doing so I configure the driver to clone the desktop and to play every video overlay fullscreen on the TV.
Is there any way of doing that in Linux? I am using the proprietary Nvidia drivers and nvidia-settings also allows me to configure cloning, but says nothing about video overlays, so the desktop is really only cloned. At the moment I extend the desktop to the TV, so that I can just drag the player window to the TV and make it fullscreen there. But I really don't like this extended screen stuff, I want my mouse cursor to stay on the primary screen.
So is there any other way of playing videos fullscreen on my TV?

thx,
fallen

---

### Post by shavenlunatic on 2007-05-17
same here, I would have liked the "drag it across to yer TV" functionality, but I can';t seem to get it right.

Best option I ended up getting was setting up your TV as a seperate x-server (option is in nvidia settings) and playing with it.  You will get basically another desktop, but if you RUN your video player from within that desktop it will play full screen and not affect your normal workspace.

Your mouse will flow between screens nicely, but unfortunately you can't drag items accross in that fashion


I'm a noob though, so there probably IS a simple way around it that I just haven't found

---

### Post by ninjaprawn on 2007-05-17
you can use twinview, which gives 1 massive desktop stretched across screens, or cloned, or and the 1 i use is traditional, this gives 2 different x servers, so both can be different resolutions, but you cant drag across screens! u have to open what u want on the correct screen.

to configure anything tho, the easyest way is with the gui when u type;

dpkg-reconfigure xserver-xorg

into terminal.

---

### Post by fenian on 2007-05-17
I use seperate X screens to view video on the TV while running other apps on the CRT monitor.To easily setup seperate X screens first install the latest nvidia drivers , you can use the [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") script to help you do this.
After you have updated your drivers open a terminal and type...
> 
gksudo nvidia-settings

the nvidia gui will open allowing you to change settings.Choose X Server Display Configuration from the left menu.Click the TV in layout then click the configure button choose Seperate X Screen.Click the save to X Configuration button at the bottom right,quit and reboot.You should now be able to launch video files (or any other app) from the TV screen,these files will only be displayed on the TV and cannot be dragged between screens.

---

### Post by lw5 on 2007-05-19
> **fenian said:**
> I use seperate X screens to view video on the TV while running other apps on the CRT monitor.To easily setup seperate X screens first install the latest nvidia drivers , you can use the [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") script to help you do this.
After you have updated your drivers open a terminal and type...


the nvidia gui will open allowing you to change settings.Choose X Server Display Configuration from the left menu.Click the TV in layout then click the configure button choose Seperate X Screen.Click the save to X Configuration button at the bottom right,quit and reboot.You should now be able to launch video files (or any other app) from the TV screen,these files will only be displayed on the TV and cannot be dragged between screens.

This doesn't sound like a solution the topicstarter is looking for. You're still working with two screens. The above might be useful to TS when launching video files from console (specifying on which screen the application should be shown, something like: 'mplayer movie.avi display=:1').

Otherwise, at least with TwinView, I don't think overlay is possible:
> 
Q: Do video overlays work across both display devices?
A: Hardware video overlays only work on the first display device. The current solution is that blitted video is used instead on TwinView.


The above is from the Nvidia driver manual: [link](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/index.html) (Appendix G.)

---

### Post by mocha on 2007-06-13
I was wondering, as a workaround to this issue, is it possible to put something in the options of mplayer or vlc to get them to display fullscreen on the secondary device?

---

