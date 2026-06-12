---
title: "After installing nVidia beta driver, GDM won't start automatically"
date: 2008-12-28
forum: Multimedia Software
---

### Post by theytookpenny on 2008-12-28
What happens is when I start up and login, the monitor turns off.

I have done the following to try and fix it:

Reset xserver-xorg and then try to install a different driver... but It still did the same thing.

So I installed the beta driver again. The only solution so far is to login using ctrl+alt+f1. I have to stop then start /etc/init.d/gdm, logout. Then login using the gui, then it goes to blank screen, then while still logged in do ctrl+alt+f1, stop and start gdm again, logout, and then my desktop shows. Any ideas?

---

