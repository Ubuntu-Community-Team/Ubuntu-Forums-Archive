---
title: "xubuntu session display corrupt"
date: 2010-10-07
forum: Multimedia Software
---

### Post by YNWA2010 on 2010-10-07
Hi, i'm sure I'm not the first to experiance this, but i dont seem to be able to find the info i need.

I have just installed ubuntu server, and intend using it for we developement and hosting. I've installed this on an old laptop (very impressed with performance). Anyway i tried to change the screen resolution from 1024x768 to something higher, but the display for the "xububtu session" became corrupt.
is it possible to edit a config file to set the display back to 1024x768 to get the gui to work again. Currently i an accessing the laptop via a ssh/telnet session.

Thanks

---

### Post by YNWA2010 on 2010-10-07
fixed the problem by doing the following from a terminal window.....

sudo service gdm stop
vi /home/<userid>/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml

(changed the display back to 1024x768)

sudo service gdm start



happy times are here again !!!

---

