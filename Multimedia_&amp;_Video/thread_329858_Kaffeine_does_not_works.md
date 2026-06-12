---
title: "Kaffeine does not works"
date: 2007-01-02
forum: Multimedia &amp; Video
---

### Post by mkanada on 2007-01-02
Kaffeine stop working in last days. xine, mplayer and others still working, so I dont think it is a codec problem. But Kaffeine icon appears for some seconds in taskbar, and so disappear. No dialog is showed, so, I dont know where I can find any errors log.

Can someone help me?

Tanks.

(kubuntu 6.10, diary updated)

---

### Post by ardnut on 2007-01-02
From a konsole window run...

killall kaffeine

then try and run kaffeine again.

I have this problem on every reboot. I have the option ticked to keep Kaffeine in the system tray but for some reason it never restores it self on a reboot.

Very annoying, any one know why this broke in Edgy?  It used to work fine in all previous Kubuntu releases.

---

### Post by ardnut on 2007-01-02
Hmm.... looks like version 0.8.3 changelog has these fixes which could answer my above issue:

* fixed: session issue.
* fixed: crash when quit from systray.

---

