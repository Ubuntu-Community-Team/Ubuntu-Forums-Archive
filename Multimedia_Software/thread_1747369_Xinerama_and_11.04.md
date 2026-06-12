---
title: "Xinerama and 11.04"
date: 2011-05-02
forum: Multimedia Software
---

### Post by _glook on 2011-05-02
I recently upgraded to Natty Narwhal. Wasn't a fan of the global menubar, so I switched back to using gnome (classic). Here is my current situation.

[LIST]
[*]Using Ubuntu 11.04 upgraded from 10.10, both 64 bit.
[*]Using classic mode (gnome).
[*]Macbook Pro dual install using refit.
[*]A vertical monitor attached.
[*]Graphics settings are using NVidia X Server settings.
[*]Did a "sudo apt-get install nvidia-current" and it told me I had the latest one.
[*]Using Xinerama; setup the macbook's screen as a 1440x900 landscape monitor with the other vertical monitor as a 1080x1920 portrait mode monitor.
[/LIST]
The main issue here is that when Xinerama is enabled, the mouse cursor is displayed like it is supposed to. However, the macbook's screen is blank otherwise (black screen) and the vertical monitor has part of it displaying the desktop that should be on the macbook screen. If I try to interact with that display using the mouse cursor, nothing happens. In order to interact with what is on the vertical monitor, I have to move the mouse cursor over to the macbook's screen and guess as to where the things I want to interact with them are. In other words, when I interact with the mouse cursor on the black screen, things happen on the other screen. This is on top of the fact that the macbook's screen's display is on the vertical monitor and that the vertical monitor's screen's display is not shown at all.

Would anyone be able to help out with this? Any help is appreciated.

---

### Post by your imaginary friend on 2011-05-07
I'm no expert but since xinerama kills compiz, and unity relies on compiz, I'm gonna guess that using xinerama kills everything.

Xinerama has never been friendly to me so I never use it.  Can you use twinview instead?

EDIT  checkout this post [http://http://ubuntuforums.org/showthread.php?t=1741188]("http://http://ubuntuforums.org/showthread.php?t=1741188")

---

### Post by hvengel on 2011-07-04
TwinView has issues under certain conditions that make it unusable.   For example TwinView does not correctly implement the X11 extensions needed to set the video card gamma table.   This makes TwinView unusable for color critical work since it is impossible to calibrate more than one monitor.  With xinerama this issues does not exist and it is possible to calibrate all connected monitors.  Nvidia has had an open bug report for this issue for almost 4 years now it is is still unresolved.

I found this thread when looking for info about how to get xinerama working with my nvidia hardware with ubuntu 11.04.  I have this working fine with the same hardware, kernel version and nvidia driver version running Gentoo on the same box.  But with Ubuntu X will not start if I enable xinerama.  Anyone have any idea how to get this working?  And I should add that I don't care if this kills  Compitz.

---

