---
title: "Framebuffer and virtual terminal"
date: 2012-09-20
forum: Multimedia Software
---

### Post by Rokel on 2012-09-20
I succeeded to make multiple X sessions on VT6-VT10 and can switch between them. 

I can run VNC sessions to each of them. 

The problem I have is that the VNC sessions only get updated if the terminal is active (visable on the physical box). If I move to  virtual terminal 8, (ctrl-alt-F8 etc.. or chvt 8  )  the other VNC sessions on VT6 9 and 10 freeze up. 
(although mouse clicks and keys seem to get through) 

I tried disabling dpms and screensavers but I guess it boils down to having more instead of one framebuffer?

---

