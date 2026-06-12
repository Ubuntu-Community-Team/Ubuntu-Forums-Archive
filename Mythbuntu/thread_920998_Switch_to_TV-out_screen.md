---
title: "Switch to TV-out screen"
date: 2008-09-15
forum: Mythbuntu
---

### Post by newlinux on 2008-09-15
I have a nvidia 7100 configured with restricted drivers to do dual out (to CRT and to TV-out). How the heck do I switch the focus to the TV out screen? I thought just using the mouse to move over would do it. I'm not using xinerama or twinview, just separate X-screens I think. This is my first attempt at this :). I know I can open up a window on the tv-out screen using -display :0.1, but how do I switch the focus?

---

### Post by newlinux on 2008-09-16
must have been something strange going on... A couple of reboots later and moving the mouse over works. Somehow the mouse was frozen to one screen!

---

### Post by Xnyper on 2008-10-28
I had the same problem a few days ago, while I was setting up my second monitor.  After playing around with nvidia-settings I was able to get the x-screens connected so that the mouse can move between them.  It seems kind of finicky.

My problem now is that I can't seem to find a way to switch focus to a window on the other monitor without using the mouse.  I'd really like an alt-tab sort of way to do this, rather than needing to move my mouse over there and click in the window just do go back to the keyboard to type in it.

I have three vim buffers open, text-editing like lightning, and then I have to move the mouse over to the other monitor, click it, and then navigate back to home row just to compile.  Gotta use the mouse again to go back to editing.  It's a real productivity killer.

Any ideas?

---

