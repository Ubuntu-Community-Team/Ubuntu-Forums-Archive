---
title: "Myhtbuntu xfce desktop via vnc"
date: 2016-10-10
forum: Mythbuntu
---

### Post by retakal on 2016-10-10
Hi,

I am running mythbuntu being connected to a projector which has only limited (very low) screen resolutions up to 1024*768. For watching TV etc it is very fine, but I also would like to remote connect to the machine via vnc in order to work on it.
From the remote machine a higher screen resolution would be possible. Using the vino-server from Gnome or x11vnc actually works, but as I log on to a running X session I am not able to increase the screen resolution. So I have a only tiny window on my remote machine which is even too small for most applications.

I guess this means I need a virtual desktop session so that I can adjust the screen resolution. I have tried several, e.g. with tightvnc or tigervnc. 
I adjusted the xstartup from ~/.vnc to this:
```

#!/bin/bash
xrdb $HOME/.Xresources
startxfce4 &

```

Then I start *tigervncserver -geometry 1920x1080*

This gives me a new virtual desktop and I can connect to it, but it is the default xfce interface even asking how I wanna configure it. 
I would like to have the same "theme" including all incons, symbols etc. of xfce for the virtual desktop as the original one. 

**Question:** How can I achieve it?

Also the workaround of manually adjusting the virtual desktop doesn't work. As soon as the vnc server is restarted I am back to a virgin xfce virtual desktop...

Thanks!

---

