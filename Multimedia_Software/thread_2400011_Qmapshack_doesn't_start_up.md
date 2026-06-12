---
title: "Qmapshack doesn't start up"
date: 2018-09-01
forum: Multimedia Software
---

### Post by livino2 on 2018-09-01
Hello,

I'm not able to start up Qmapshack in Ubuntu 18.04. It was no problem until one week ago, so maybe some software update causes the problems?

I don't know where to start looking in my system, so who can give me some ideas to work it out?

Lieven

---

### Post by Yellow Pasque on 2018-09-01
Try starting it from the terminal and see if you get any informative errors. "It doesn't start" doesn't give us much to go on.

---

### Post by livino2 on 2018-09-03
> **Temüjin said:**
> "It doesn't start" doesn't give us much to go on.

I know :-/ . That's why I asked how I could find more information about the problem myself ;-)

Anyhow...

When I start it via the shortcut, after a few minutes I get an error report.

[IMG]https://c2.staticflickr.com/2/1896/30573589058_f72b72f044_o.png[/IMG]

I tried running it via the terminal by using the command 'qmapshack' (I'm not sure if it is the right command...).

This is what I got:

```
2018-09-03 9:58:25.146 [warning] "no file found for translations '/usr/share/qt5/translations/qt_nl' (using default)."
2018-09-03 9:58:25.673 [warning] libpng warning: iCCP: known incorrect sRGB profile
2018-09-03 9:58:25.676 [warning] libpng warning: iCCP: known incorrect sRGB profile
pure virtual method called
terminate called without an active exception
Afgebroken (geheugendump gemaakt)
```

In case you don't understand Dutch, the last line means something like "aborted, made a memory dump".

Does that give more information?

Lieven

---

### Post by Yellow Pasque on 2018-09-03
The first thing I would try is running the program as a different user or guest. It's possible there is some saved data/configuration in your home directory that is causing the crash.

Other than that, it is difficult to troubleshoot:
[https://bitbucket.org/maproom/qmapshack/wiki/TroubleShooting#markdown-header-create-a-backtrace-of-a-crash-on-linux](https://bitbucket.org/maproom/qmapshack/wiki/TroubleShooting#markdown-header-create-a-backtrace-of-a-crash-on-linux)

---

