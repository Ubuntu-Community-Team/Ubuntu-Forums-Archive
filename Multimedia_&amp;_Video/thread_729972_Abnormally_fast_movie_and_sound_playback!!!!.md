---
title: "Abnormally fast movie and sound playback!!!!"
date: 2008-03-20
forum: Multimedia &amp; Video
---

### Post by redhairfreerider on 2008-03-20
Hello, after installing the driver for my EMU 0404 I ve found out that both sound and video playback run faster than normal and this happens with all players I have tried VLC,mplayer,audacious!Please help....

---

### Post by uBeer on 2008-03-27
The problem: the clock of your soundcard is still on 48kHz.
The solution: change it to 41kHz
A way to do it: if you open the properties of your sound (by double clicking the icon in the systray for example) you can click Edit -> Preferences and in the screen that you'll get you'll have to find the entry that says: "clock internal rate". Select that one. Now there's an extra tab in the sound preferences where you can select at which rate you want to play stuff. Hope that helps.

There still a problem with rates other than 48 and 41 because it hasn't been implemented yet. But I'm more than happy to get at least some sound out of my EMU :D

---

