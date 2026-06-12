---
title: "Separate X Screen for Dual NVIDIA system?"
date: 2008-07-01
forum: Multimedia Software
---

### Post by frozenjake on 2008-07-01
Hi all, I know this might be a n00b question, but I have searched steadily and found nothing that helps. I have a Dual Nvidia setup w/8800 GTX (Primary) and a 8600 GT, the 8600 is used just for my TV (Svideo/Component) other is on a Viewsonic HD display.
In the GUI X.org configurator It recognizes my 2nd vid card and gives me all the thermal/proc meters, and even recognizes that there is a TV attached (calls it TV0) but it won't let me use it! It shows TV0 as disabled and when I try to activate it as a separate X screen (TwinView is grayed out, which is fine) it just ignores me and keeps it disabled! How can I force the system to activate it? Hell at this point i would even be happy with TwinView.
I tried creating entries in the Xorg.conf file for another X screen, and to define my second video card etc. No luck. It works fine in Windows..but ugh....I hate windows.

Any help?](*,)

---

### Post by NT4usB on 2008-07-01
Sounds like you don't have permissions to make changes.
Have you tried```
sudo nvidia-settings
```
Post your xorg so we can see what you've done to it.

---

