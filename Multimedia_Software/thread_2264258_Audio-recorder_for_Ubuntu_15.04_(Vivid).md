---
title: "Audio-recorder for Ubuntu 15.04 (Vivid)"
date: 2015-02-06
forum: Multimedia Software
---

### Post by osmoma on 2015-02-06
Audio-recorder v1.6-0 is now ready for Ubuntu 15.04 alpha (Unity Desktop).
You are welcome to use it.
[[IMG]http://bildr.no/thumb/UEN6cUdH.jpeg[/IMG]]("http://bildr.no/view/UEN6cUdH")

ChangeLog:
 * Version 1.6-0.
  * Improved, automatic installation of missing plugins. Configuration (configure.ac) needs now  
  * gstreamer-pbutils-1.0 library and compilation needs libgstreamer-plugins-base1.0-dev package.
  * Removed deprecated GTK 3.14 functions. 
  * Removed support for GtkStatusIcon class in systray-icon.c file (we now support only AppIndicator).
  * Fixed the level-bar widget (for GTK 3.14). User can change the bar style by left/right clicking on the widget.  
  * Handle multiple timer commands better (changes in timer.c). 

Source code:
[https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)

Packages for Ubuntu, Mint:
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)

**Notice**: I have not generated packages for Ubuntu 14.10. Users of Ubuntu 14.10 get the slightly older audio-recorder v1.5.  
It"s perfectly alreit for recording.   However, you can compile a.r from source on Ubuntu 14.10 too.

This new version can be compiled and run on any modern Linux-distro that has GTK 3.14+ and Gstreamer 1.4.
[[IMG]http://bildr.no/thumb/OVo2UTVn.jpeg[/IMG]]("http://bildr.no/view/OVo2UTVn")

Obrigado e boa sorte amigos !
  Moma, 
Palmela/Portugal.

---

### Post by MartyBuntu on 2015-02-06
An excellent application. I've had it installed and use it for half a year now.

Best of luck with your future developing!

---

### Post by keith-k on 2015-03-23
> **osmoma said:**
> Audio-recorder v1.6-0 is now ready for Ubuntu 15.04 alpha (Unity Desktop).


Packages for Ubuntu, Mint:
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)
.


I get a "You are not allowed to view this page." page when I click that link.

very sad

---

### Post by MartyBuntu on 2015-03-24
Works for me. Try again.

---

