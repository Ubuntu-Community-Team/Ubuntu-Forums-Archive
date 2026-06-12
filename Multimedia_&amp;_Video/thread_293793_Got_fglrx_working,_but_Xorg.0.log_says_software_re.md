---
title: "Got fglrx working, but Xorg.0.log says software rendering"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by rmjb on 2006-11-05
Hello,

I got my fglrx to work in Edgy by following method 1 on this link:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

And it works since glxinfo says direct rendering: Yes and fglrxinfo returns ATi instead of Mesa.

However, when I took a look at my Xorg.0.log I see the following lines:
```
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
```

Anyone know's why? Also, what can tell me definitively if I'm using software or hardware rendering?

- rmjb

---

### Post by AlberTUX-CRC on 2006-11-15
I have the same problem. running on a dell latitude D600 with ATI radeon 9000.

i also have problems shutting down after driver installation. :confused:

---

### Post by whatever on 2006-11-15
(EE) **AIGLX**: reverting to software rendering

the fglrx driver does not support AIGLX

---

### Post by rmjb on 2006-11-15
Okay, if that's all it means then I guess we're cool.

- rmjb

---

