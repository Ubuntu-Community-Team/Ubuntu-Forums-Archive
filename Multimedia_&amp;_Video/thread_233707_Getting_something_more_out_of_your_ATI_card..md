---
title: "Getting something more out of your ATI card."
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by RudolfMDLT on 2006-08-10
Hi there! 

I stumbled onto a post about a guy who had trouble getting his screen savers working smoothly. I had the same troubles but never gave it a second thought. Adding the following one line to your /etc/X11/xorg.conf "Device section" can improve your graphics a lot! It won't show any difference in glxgears but it did improve my screen savers and should help with some other graphics intensive stuff too! Just though you guys ought to know about it! :D 

> Option "AGPMode" "4"

Just save a backup first!

---

