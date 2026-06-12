---
title: "Video problems"
date: 2009-02-20
forum: Multimedia Software
---

### Post by Hansa91 on 2009-02-20
Hello, I'm not very familiar with Ubuntu, and I'm having a little problem with videos. I get screen tearing and blinking in the player window.
Do anyone know how to fix this problem?

I'm using Ubuntu 8.10 (Intrepid Ibex), I have the Ati drivers installed, and my graphics card is HD3870.

---

### Post by Mercury_Alpha on 2009-02-20
There appears to be a problem with ATI cards and compositing (like compiz-fusion, for example). When compositing is enabled, videos won't play properly. There are two ways around it: Disable compositing or use software-based rendering for your videos. Some video players don't let you choose which rendering mode you use. VLC is one that does.

If you want to disable compositing, go to System>Preferences>Appearance, click on the Visual Effects tab, and choose "None."

---

