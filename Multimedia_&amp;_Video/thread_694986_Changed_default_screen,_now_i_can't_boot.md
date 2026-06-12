---
title: "Changed default screen, now i can't boot"
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by vladu on 2008-02-12
Hi!

A little while ago, I reported a bug ( [https://bugs.launchpad.net/bugs/141248](https://bugs.launchpad.net/bugs/141248) ) about the "Screens and Graphics" window (from System->Administration->~). 

Today I went back to play a little with the settings, I changed the Default screen to Screen2. I logged out but the welcome screen didn't show up. Instead I only had a black screen with a small prompter in the upper left corner. I can't go to a terminal screen (pressing Ctrl+Alt+F1), i can't do anything, although the keyboard is not dead (caps lock led works correctly)

So i'd like two things:
1. to draw attention upon the "Screens and Graphics" window - it really doesn't work as it should (And speaking of that, how should it work? why do we have this and also in Preferences->Screen Resolution?)

2. get back my system. What is the file that "Screen and Graphics" edits and how can I modify it back?

thanks!

---

### Post by jan quark on 2008-02-13
try to run this command

automatic xserver configuration
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

manual xserver configuration
```
sudo dpkg-reconfigure -plow xserver-xorg
```

choose one and then run

```
startx
```

the file is probably the xorg.conf

you can edit it with

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by vladu on 2008-02-15
Hi

I was busy with some exams, but today I took a little time and fixed the problem. Here's how i did it:

jan quark, you were right, it was *xorg.conf*. Unfortunately I could only access my disk from the live cd, so running any of your code would have modified only the live session's files. 

Instead, I copied the *xorg.conf* of the live session over my old broken *xorg.conf*. The first restart was a bit ugly because after a couple of minutes of blank screen (while booting), my system restarted by itself. Luckily, I had to leave a little, and when I came back, my system was working - with the default video drivers, but that was easy to fix.

Thanks!

---

