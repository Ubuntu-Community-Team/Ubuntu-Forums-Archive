---
title: "A command for switching mode with nvidia?"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by mviroli on 2007-04-24
It is a matter of fact that the Ctrl-Fn8 key is not switching graphics mode very well on many laptops with the nvidia card and driver, e.g. on my DELL D620.
However, I was observing that the nvidia-settings application is able to correctly send switching commands to the driver: each time a new mode is applied through that application, things switch perfectly and a new line of the kind

(II) NVIDIA(0): Setting mode "1280x1024"

appears on the X log file.

So, I'm wondering whether there is a command from the terminal which I can use to tell the driver to switch to a new mode specified in the xorg.conf file. (Using nvidia-settings each time is not very practical..)
Thanks for any help.

---

