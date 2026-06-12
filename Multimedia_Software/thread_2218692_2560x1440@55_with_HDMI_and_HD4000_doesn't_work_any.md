---
title: "2560x1440@55 with HDMI and HD4000 doesn't work anymore (13.10 -&gt; 14.04)"
date: 2014-04-21
forum: Multimedia Software
---

### Post by a_kemper on 2014-04-21
Hi,

after upgrading Ubuntu from 13.10 to the latest version, I'm not anymore able to drive my external display with native solution, connected via HDMI-DVI-cable. Using the tweak described in [http://www.notebookcheck.com/2560x1440-oder-2560x1600-ueber-HDMI-ansteuern.89837.0.html](http://www.notebookcheck.com/2560x1440-oder-2560x1600-ueber-HDMI-ansteuern.89837.0.html) this was possible for my ivy-bridge notebook with HDMI-only output. In contrast, when finally triggering "xrandr --output HDMI1 --mode 2560x1440" the display gets shortly blanked with the message "xrandr: Configure crtc 0 failed". In Xorg.log the following lines can be found:

> 
[ 27635.065] (II) intel(0): resizing framebuffer to 2560x1440
[ 27635.067] (II) intel(0): switch to mode 1920x1200@60.0 on HDMI1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 27635.099] (II) intel(0): switch to mode 2560x1440@54.9 on HDMI1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 27635.496] (EE) intel(0): failed to set mode: Invalid argument
[ 27635.548] (II) intel(0): resizing framebuffer to 1920x1200


Any idea for new valid arguments or additional changes required?

Thanks in advance,
Andreas

---

