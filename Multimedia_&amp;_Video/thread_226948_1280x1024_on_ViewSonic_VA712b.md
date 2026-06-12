---
title: "1280x1024 on ViewSonic VA712b"
date: 2006-07-31
forum: Multimedia &amp; Video
---

### Post by blicksky on 2006-07-31
I'm trying to get my ViewSonic VA712b monitor to display 1280x1024 on my Dell Latitude C800 with an ATI Rage Mobility M4.  On the built-in LCD, I can set the resolution to 1024x768, 1280x1024, and 1600x1200.  When I switch to the external LCD using Fn-F7 when set to 1024x768, it displays fine, but when set to 1280x1024 (the VA712b's native resolution) it just displays "Out of range".  I've tried adding all kinds of mode lines and frequency ranges to the Monitor section of xorg.conf, but nothing has worked.  Can anyone help my get my external LCD to display at 1280x1024?

---

### Post by Dylan103 on 2006-08-01
System > Prefrences > Screen  Resolution change it to 1280x1024.

---

### Post by tseliot on 2006-08-01
Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by blicksky on 2006-08-02
Thanks for those resources, tseliot, but unfortunately I still haven't been able to get it to work.  No matter how I have xorg.conf configured, the external monitor continues to say "out of range" when I set the resolution to 1280x1024.  If anyone else has any suggestions, I'd really appreciate it.

---

