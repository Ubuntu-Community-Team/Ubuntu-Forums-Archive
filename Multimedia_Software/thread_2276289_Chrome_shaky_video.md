---
title: "Chrome shaky video"
date: 2015-05-01
forum: Multimedia Software
---

### Post by michael-piziak on 2015-05-01
On some websites, Google chrome plays the videos too shaky.  For example, on NHL.com (or facebook).  You tube works fine though.  I have Ubuntu restricted extras installed and flash player installed.

Anyone else experience this?   Works fine in Firefox though.

---

### Post by Vladlenin5000 on 2015-05-04
Indeed. Just tested and confirmed your findings. Here's the conclusions:

1. YouTube works fine because in Chrome it defaults to HTML5 (you can also force it to HTML5 under Firefox in the newer versions, without any third-party extensions).
2. NHL.com uses the old Flash and it has a problem with the latest version, at least; Firefox is stuck at 11.2, the last Flash version officially supported in Linux (Google Chrome is an exception because due to a special agreement with Adobe, Chrome ships with the same Flash version available for Windows (17.0.0.134)). I haven't tested Facebook videos.

The problem only occurs when using newer Flash versions. This says a lot about those websites... And Adobe Flash.

---

### Post by monkeybrain20122 on 2015-05-04
Just checked NHL and facebook. I cannot reproduce your issues, no problem at all here. Chrome [COLOR=#303942][FONT=Ubuntu] 42.0.2311.135 (64-bit)[/FONT][/COLOR], Ubuntu 14.04.2 64 bit.

---

