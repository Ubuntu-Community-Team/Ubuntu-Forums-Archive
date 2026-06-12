---
title: "Dual monitor setup"
date: 2010-02-18
forum: Multimedia Software
---

### Post by dimoftheyard on 2010-02-18
I've played around with a second monitor, but so far I haven't found a satisfying solution. I am using a laptop with a GeForce 9600M GS graphics card. I have managed to set up twinview, but my monitors don't have the same height so I'd rather have something like the "seperate x screen" option. Or how I imagine that option would be like :)
After some problems with the nvidia configuration tool (I couldn't change the xorg.conf, until I read this:  [http://ubuntuforums.org/showthread.php?t=1373576](http://ubuntuforums.org/showthread.php?t=1373576)) I now have two seperate screens, but the second one is all empty, with black background and X-shaped mouse cursor. There seems to be no window manager running, I can start programs there with -display :0.1 , but they don't get any frame decoration and, which is worse, no keyboard focus. I'd be fine with a fullscreen konsole there, so I don't really need a window manager, but I do need access from the keyboard.

Does anybody know a solution to that problem, or can recommend another setting for dual monitors? I've read about various, but I found it hard to guess how they might behave. I'd prefer a setup that would allow me to easily (without editing xorg.conf) switch between using both monitors and using only one, because I don't always use the laptop at home.

Thank you for reading this, and thank you even more if you're considering giving me an answer.

---

### Post by darkenvy6 on 2010-05-07
Any solution to this problem? I have the same issue but on 10.04

---

### Post by JwB Zoofware on 2010-05-10
I'm also having the same problems and would be grateful if any one could help?

As per the OP, just being able to get keyboard focus on the secondary screen would be fine.

---

### Post by JwB Zoofware on 2010-05-10
For anyone who's interested, the solution for getting keyboard focus in the second display is to load up a new window manager in that display.

I'm not sure about gnome, but KDE doesn't support multiple instances, so a separate window manager is needed.

[http://en.gentoo-wiki.com/wiki/X.Org/Dual_Monitors#Independent_Dual_Head_in_KDE_4.2](http://en.gentoo-wiki.com/wiki/X.Org/Dual_Monitors#Independent_Dual_Head_in_KDE_4.2)

---

