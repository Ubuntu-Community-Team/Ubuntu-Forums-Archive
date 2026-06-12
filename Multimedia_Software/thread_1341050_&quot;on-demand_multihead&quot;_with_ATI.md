---
title: "&quot;on-demand multihead&quot; with ATI?"
date: 2009-11-29
forum: Multimedia Software
---

### Post by mkaut on 2009-11-29
Hello,

I have two 1280x1024 monitors, where the idea is to use the second on only when I need extra space (like photo-editing in Gimp). In other words, I want to be able to switch between one-monitor and multihead (extended) desktop without reboot. I found that I can easily do this with xrandr, the only thing I needed was to make an xorg.conf file (in Karmic, it does not exist by default) with "Virtual 2560 1024" line in Display SubSection. With a simple script to switch between the two modes and a launcher on the panel, it works very nice.

The problem is that this way I do not get any 3D acceleration. When I turn on the ATI Catalyst driver, on the other hand, I it needs restart to change the settings and xrandr wouldn't help, as it sees only one screen/output 2560x1024.

So, my question is whether there is some way how to get 3D-acceleration (at least on the main monitor) and the possibility of mode-switching without restart at the same time?

(I have even tried the newest drive from ATI webpage. It did not solve the issue. In addition, it always started with both monitors ON and in clone mode, so I removed it..)

Thanks

Michal

---

