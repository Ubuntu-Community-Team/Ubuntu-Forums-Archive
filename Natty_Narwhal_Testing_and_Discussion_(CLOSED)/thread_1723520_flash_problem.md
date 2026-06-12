---
title: "flash problem"
date: 2011-04-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by TDK800 on 2011-04-07
Instead of flash video player Firefox shows an empty black box, closing all Firefox windows and restarting Firefox fixes it. Anyone else experiencing this?

[IMG]http://img560.imageshack.us/img560/8829/flasherror.png[/IMG]

---

### Post by Yumi on 2011-04-07
I can not find a flash add-on for firefox. Offers deb for 9.04! How does restart fix the problem? You must have an extension installed.

Michael

---

### Post by cariboo on 2011-04-07
Flashplugin-installer usually installs the correct 32-bit flash plugin. If you have problems installing flash, have a look at lovinglinux's [flash-aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") add-on.

---

### Post by rburkartjo on 2011-04-07
the flash aid ext worked for me

---

### Post by TDK800 on 2011-04-07
I have the "Adobe Flash Plugin" installed through Software Center. It worked fine for years, until recently... the problem seems to be caused by "flash overload" - when one or more browser windows are open that contain a lot of flash elements. The "fix" is closing all browser windows and opening only the youtube page with flash video player.

---

### Post by rbrick49 on 2011-04-07
I tried playing video on chromium as firefox was flickering chromium works just fine

---

### Post by Kirk M on 2011-04-08
> **cariboo907 said:**
> Flashplugin-installer usually installs the correct 32-bit flash plugin. If you have problems installing flash, have a look at lovinglinux's [flash-aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") add-on.

That's exactly what I did. I'm running a fully updated Natty amd64 and the default Flash plugin was causing certain embedded videos to breakup (Google News shows this really well) as well as Flash based web apps and games. The Flash Aid extension for Firefox that [COLOR=#d40000]**cariboo907**[/COLOR] mentions solves this problem nicely. For me it removed the default Flash non-free installer and installed the latest 64 bit Flash plugin (beta  build-version 10.3 d162) and now embedded videos and Flash based web games and apps run fine--no anomalies.

---

### Post by Yumi on 2011-04-08
Thanks. For me flash-aid solved the problem. Whatever it installed or removed, flash is working now on Firefox 4.

Michael

---

