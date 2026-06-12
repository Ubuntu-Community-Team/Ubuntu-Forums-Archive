---
title: "Incorrect screen resolution/unknown monitor 10.10"
date: 2010-10-03
forum: Multimedia Software
---

### Post by dabbi2000 on 2010-10-03
Hi,
my mediocre Linux skills are lacking and I need you help with fixing this problem of incorrect resolution on my laptop after updating 10.04 to 10.10.

-In Preferences/Monitors I get "monitor unknown" and I am stuck with a 1024x768 resolution while my monitor is automatically detecting 1400x900, making a huge black border on right and bottom.

-Xandr says:
"Failed to get size of gamma for output default
Screen 0: minimum 1024x768, current 1024x768, maximum 1024x768
default connected 1024x768+0+0 0mm x 0mm
  1024x768 0.0*"

-The monitor is a "HP w1907v", the laptop a "Compaq nx9030"

-Running dcprobe it actually has the monitor name correct!

-Maybe it helps to know that on 10.04 there was some installation crack so that I would have to boot into failsafe mode every time, running some "minmal X server graphics mode" (maybe my default X config file is corrupt?)
I know the video card max resolution is 1024x768 so I would think the solution is to make the video card and monitor sync, maybe the zero refresh rate is the problem??


Any suggestions or a step-by-step guide to debug this?

---

