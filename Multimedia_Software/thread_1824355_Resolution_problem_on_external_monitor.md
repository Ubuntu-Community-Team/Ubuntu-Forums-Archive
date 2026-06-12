---
title: "Resolution problem on external monitor"
date: 2011-08-13
forum: Multimedia Software
---

### Post by evaldasp on 2011-08-13
Hello,

I have got a problem, I've connected an external LCD to my toshiba laptop 27" HP full HD monitor via HDMI port, when I set full hd resolution it bacomes black, then I have downloaded ARandR (it uses XrandR  X Resize, Rotate and Reflect Extension ) application and it looked alright, but after restart old resolution come back, how to change it permanently? I set internal monitor to off,

---

### Post by honeybear on 2011-08-25
> **evaldasp said:**
> Hello,

I have got a problem, I've connected an external LCD to my toshiba laptop 27" HP full HD monitor via HDMI port, when I set full hd resolution it bacomes black, then I have downloaded ARandR (it uses XrandR  X Resize, Rotate and Reflect Extension ) application and it looked alright, but after restart old resolution come back, how to change it permanently? I set internal monitor to off,

I would like to ...

what does give : 

```
find /etc -iname "*xorg.conf*"
```

---

### Post by realzippy on 2011-08-25
You need the xrandr commands arandr used,and copy them to xinit.

---

