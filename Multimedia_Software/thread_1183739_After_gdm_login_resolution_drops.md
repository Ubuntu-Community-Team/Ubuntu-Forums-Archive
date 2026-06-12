---
title: "After gdm login resolution drops"
date: 2009-06-10
forum: Multimedia Software
---

### Post by dandandan on 2009-06-10
Hi

I have a monitor capable of doing 1920*1200.
I can set that via the nvidia-settings tool(saved to xorg.conf of corse)
After login out and login in resolution goes back to 1280*1024, although gdm itself is in the correct resolution. 
Funny thing is that when i am using 2 monitors the resolution of the primary screen works perfect on login, when i disable the second monitor tho, resolution drops to 1280*1024 again.

Here is my xorg.conf
[http://nopaste.com/p/arCkqkdnmb](http://nopaste.com/p/arCkqkdnmb)
and my Xorg.log
[http://nopaste.com/p/a05g9g0slb](http://nopaste.com/p/a05g9g0slb)

Note that the last line is the manual change via nvidia-settings while the line before happens autopmatically on login.

Does anyone have an idea why that happens and how i can stop that?

-dan


edit: when logging in with a different user or with a different windowmanager/de all works fine, seems to be a gnome setting somehwere? Maybe from the screen resolution prefrences setting from 8.10?

---

