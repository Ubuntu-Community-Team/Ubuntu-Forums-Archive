---
title: "Can't Enable OpenGL Compositing Kubuntu 13.10"
date: 2014-01-17
forum: Multimedia Software
---

### Post by james-auble2 on 2014-01-17
When I go to change compositing in System Settings > Desktop Effects > Advanced to any of the OpenGL options the screen will flicker and I get a notice at the top saying that a couple of the effects will not work because they need OpenGL. The drop menu will show OpenGL, but once I back out of the Desktop Effects section and return to it, the option has reverted back to Xrender.

lspci | grep VGA shows: ```
james@james-X45C:~$ lspci | grep VGA00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)

```

My KDE version is 4.11.3.

I'd really like to get OpenGL working because I'm having bad tearing issues in VLC. 

Thanks!

Edit: Gave up and switched to Xfce using Compton compositor. No tearing issues now.

---

