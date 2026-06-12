---
title: "Really odd image displayed after upgrade"
date: 2008-04-26
forum: Multimedia Software
---

### Post by plusbryan on 2008-04-26
I had Ubuntu 7.latest installed and decided to upgrade to 8 today. Everything went smoothly, but when gnome loaded, I go this extremely odd screen. I don't know these kids, nor have ever seen this picture.

[IMG]http://www.collaboract.net/ubuntu/weird.png[/IMG] 

The entire portion of the screen containing the random picture was somehow overlayed over the desktop and could not be moved. Even switching workspaces did nothing.

Restarts did nothing. Then I realized it might have something to do with my xorg.conf config file, which I modified in 7 to support my dual monitors. Removing the Virtual 1600 x 2400 (or whatever it was) did the trick after an X reboot. I don't know if maybe I clicked to accidentally keep my xorg.conf file on upgrade.

So, problem solved, but I thought I'd post this screenshot because the screen that resulted was so strange.

---

