---
title: "multi-gpu multi-monitor ATI"
date: 2009-11-03
forum: Multimedia Software
---

### Post by False Dmitry II on 2009-11-03
Alright, so I've got a system with onboard 3200 HD graphics that I use to run a secondary monitor.

My main monitor is on my HD 4850 card. They both use the same driver so it should be easy to replicate (hopefully even better) what I have it doing in windows.

When it first came up, only the secondary monitor was running at all. I had to install the restricted driver, and then run CCC administratively. (Which has a bug, clicking on administrative results in it telling me the executable does not exist and then dies. I found out what the normal one is and simply ran 'sudo amdcccle' to get actual access.)

At that point I was only able to turn my main monitor on. It does work, but rather oddly. It's acting like I have 2 single monitor multi-desktops. So I've got 2 workspaces on each monitor. I can't do anything between monitors other than move the mouse between them.

What I wanted to be able to do is to just have one workspace per monitor and apparently have it be aware of each other, because it seems like it isn't.

---

### Post by markbuntu on 2009-11-03
You need to turn on xinerama for that. 

The release notes state that you may lose your window manager using some multi-gpu configurations though so you may have some problems with that, but you may not.

---

