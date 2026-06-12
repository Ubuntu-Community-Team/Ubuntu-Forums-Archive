---
title: "Screen resolution / refresh rate"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by Forceflow on 2006-12-02
Hi there,

I'm using Edgy (6.10) and I managed (after a couple of ubuntu re-installs and a lot of fiddling around - linux newcomer here) to install teh ATI X.org binary drivers, and setting up a dual-screen system. By using aticonfig --initial=dual-head.

Now, I'd like to have my first monitor (screen 0) at a resolution of 1152*864. If I use the screen resolution changer (accesed through the ubuntu menu), I can pick this resolution, but the refresh rate is too low (60 Hz). I know my screen can handle this, because it runs at 1152*864 (75 Hz) in Windows.

Is there any way to change this ?
I don't see how the ATI settings in my xorg.conf affect the screen resolution dialog. It all stays the same, appeareantly.

Here's my xorg.conf: [http://users.pandora.be/history/backup/xorg.conf](http://users.pandora.be/history/backup/xorg.conf)

---

### Post by drphilngood on 2006-12-02
See here:

[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973").

---

