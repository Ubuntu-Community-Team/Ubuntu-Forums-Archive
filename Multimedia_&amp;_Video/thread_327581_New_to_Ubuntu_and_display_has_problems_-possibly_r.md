---
title: "New to Ubuntu and display has problems -possibly refresh rate"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by TheNomad on 2006-12-29
I broke down and installed ubuntu on a considerably old intel box. CPU speed is slightly below 1Ghz. According to device manager, I have Intel 82815 CGC graphics chipset, which is the onboard video controller. I am also using a Caompaq P110 monitor through a compaq 8 port KVM switch.

I booted up to the live cd of version 6.10 that I d/l ed yesterday from the ubuntu.com website. So I am assuming, drivers are all there, especially for generic intel chipsets.

As soon as the live cd booted, and X11 started, I saw vertical blue lines about 1 inch apart on the desktop. When I open the browse, the blue lines seemed to be overlapped by the window's white bkgr, but where they are supposed to be, I now see ghosting effects where the line is supposed to pass. And still, portions of this page where the color matches to the default beigey/brown wallpaper, I still see the blue lines over the browser window. 

Can anybody tell me how can I get rid of these lines. This very same box, used to run Fedore core 5 up until 2 months ago. I unplugged the thing during a office re-build out and yesterday decided to plug it back in and put ubuntu on. While it ran fedora, I did not have any problems with video. I am a unix guy but mainly a command line type of guy and deal with unix versions you pay through the nose for licencing (can you say HP and IBM) so, I do not have extensive experience with Linux but if you direct me to the right places, I think I can find my way.

Thanks in advance

Mel

---

### Post by TheNomad on 2006-12-29
Well, I think this is a little beyond refresh rate issue. When I launched the screen resolution change utility from the system --> preferences menu, I was offered a second choice of 60 hz instead of the currently running 75 Hz. When I selected 60, the thickness of the blue lines diminished a little but they are not totally gone.

I found the /etc/X11/xorg.conf file but have no idea how to tweak it to fit my monitor and graphichs chip set. In the screen section, it seems like both the monitor and the chipset got identified correctly.

Any help is greatly appreciated.

---

### Post by wil on 2007-01-23
I fixed this by changing the DefaultDepth to 16 in the /etc/X11/xorg.conf file

---

### Post by josesanders on 2007-01-23
Are you still running from the live CD?

I can't totally picture what's going on from what you describe, but it sounds like a problem that I had when I tried changing the screen resolution and refresh rate.  I just rebooted.  If you are using the live CD still, that obviously isn't an option since it would just boot up the same as before.  Maybe you can try using CTRL+ALT+Backspace to restart the X session.

---

### Post by TheNomad on 2008-03-11
Changing DefaultDepth from 24 (system instated) to 16 in the /etc/X11/xorg.conf file was the trick. I did this long time ago but did not update the post to help others at that time. This morning I gave my old box to a colleague of mine at the office and he ran a screen configuration utility and messed it up. So I had to dig up this post and realized my selfishness.

Hope this helps someone some day.

---

