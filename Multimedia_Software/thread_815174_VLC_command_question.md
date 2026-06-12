---
title: "VLC command question"
date: 2008-06-01
forum: Multimedia Software
---

### Post by JerecDrak2 on 2008-06-01
Hi, after upgrading to Hardy, the playback of DVDs no longer worked in VLC. I would get bright green/purple blocks everywhere and there would be lots of skipping. I solved this by changing the %u argument to %m in VLC's launcher, but I can't find out what the meaning of either argument is anywhere, does anyone know where to find the information or know why changing that argument helped? I like to know what I'm changing and why these things work, thanks :)

---

### Post by mc4man on 2008-06-01
here you can read about .desktops which the launch comm. is related to.
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html)
%m has been deprecated for some time, here's description
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-0.9.3.html#exec-variables](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-0.9.3.html#exec-variables)
I found the %U worked but that disc navigation was flaky or broken, using 
%m (either from launch comm. or in the 2 vlc.desktop) navigation is perfect. Why I'm not sure, you can infer some things from reading the specs, though alot goes well over my head.

---

