---
title: "Inconsistent Performace after Proprietary Driver Install."
date: 2009-02-06
forum: Multimedia Software
---

### Post by psychobot on 2009-02-06
I've recently installed the FGLRX driver with the help of the hardware driver detection tool. Everything seems to have installed correctly. The problem I'm having is that graphics performance seems to lag at times and excel at others. Before installing the driver, glxgears shot back ~3.7k fps, consistantly. After the install, it shoots back inconsistent benchmarks between 1k and ~5k usually sitting somewhere around 2k fps. Does this sound normal or is there some editing I need to do? Please let me know what information I need to give to be helped with this matter.

thank you

---

### Post by markbuntu on 2009-02-06
glxgears is more dependent on your cpu than your gpu. If the cpu is busy glxgears will be low. 

There is the Catalyst Control Center in your menus that you can use to make performance adjustments to the flgrx driver. They do make a difference.

I can change glxgears from 59 to 2500 by adjusting the CCC settings with my HD3650 card.

---

### Post by psychobot on 2009-02-06
I went through CCC and adjusted all the settings. None of the setting make any difference with glxgears. the only difference is that i can't play any games. all i see is a bunch of flickering colors.

---

