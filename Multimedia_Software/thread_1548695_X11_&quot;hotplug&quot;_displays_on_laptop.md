---
title: "X11 &quot;hotplug&quot; displays on laptop"
date: 2010-08-08
forum: Multimedia Software
---

### Post by nerr on 2010-08-08
I have a Dell Studio XPS 13 laptop with an NVIDIA GPU, and VGA, HDMI, and DisplayPort outputs, and I have recently become interested in the possibilities of connecting my laptop quickly and easily to an external display (as I am able to do with Windows 7 :P).

What I really like about Windows is that I am able to plug in a display, and the operating system is able to seemingly remember a certain profile for any given display that I plug into it.  An example follows:

I have three external displays, which may be used at varying times.

1x 17" LCD (1280x1024)
1x 24" LCD (1920x1200)
1x 47" HDTV (1920x1080)

Whenever I plug any of these devices into my machine while running Windows, it is able to automatically detect the last settings for each display, and extends my desktop as such.  As soon as the display is unplugged, my mouse cursor and other windows can no longer travel outside of the bounds of my 1280x800 display on my laptop.  In Ubuntu, I am able to make my 24" display work perfectly over HDMI, but I'd like its X Screen to be completely disabled whenever the device is unplugged.  This way, the window/cursor can leave the bounds of my main screen when I am on-the-go with my laptop as opposed to sitting at my desk with my 24" screen.

EDIT: I do realize that I can modify the NVIDIA X Server Configuration, disable the X Screen, then exit to terminal and restart X, but this is fairly complex and not as simple as I would like it to be for a college student who often moves around frequently with his laptop.

Is it possible to modify a setting in /etc/X11/xorg.conf or possibly the NVIDIA X Server Configuration panel to allow for this functionality?  Any help would be much appreciated, thanks!

---

