---
title: "Quick way to change NVIDIA Settings?"
date: 2009-11-06
forum: Multimedia Software
---

### Post by brad_richards on 2009-11-06
I use my laptop (Jaunty 9.04) for presentations, and recently installed the proprietary Nvidia drivers. This means that, to connect to the projector, I have to use the "NVIDIA X Server Settings" tool. In order to get the proper configuration, I have to follow a ridiculously complex procedure:

1. Open the tool, "detect" monitors, select twinview, set resolution to *off*, select the normal laptop screen, mark it as primary display, apply. (Without this, the system menus move to the projector).

2. Then finally, what you expect: select the projector, select the resolution, and apply

This is a pain, when you get to do it several times a day. Does anyone have a better solution? A way to automate this?

Thanks,

Brad

---

### Post by Jenkins1 on 2009-11-06
Hi,

I have a laptop that is connected to an external monitor, I often take it to lectures/labs etc.

I used this thread [http://ubuntuforums.org/showthread.php?t=1114767&highlight=disper](http://ubuntuforums.org/showthread.php?t=1114767&highlight=disper) 
[http://willem.engen.nl/projects/disper/]("http://willem.engen.nl/projects/disper/") disper project page


I have a script biased on the one in the above thread that runs at login. It specifically looks for my external display and if any other display is connected then it clones rather than extending the desktop. Unfortunately as disper does the changes, at least in my case the screen does go black or show the desktop in a muddled puzzle like form. As this is only for 2 seconds its not really a problem. I have also got the script linked to a keyboard shortcut if i forget to plug my monitor in.

Hope this helps

---

