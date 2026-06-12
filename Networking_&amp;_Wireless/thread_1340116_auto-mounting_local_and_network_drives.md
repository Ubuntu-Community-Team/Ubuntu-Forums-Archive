---
title: "auto-mounting local and network drives"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by Matt26 on 2009-11-28
i was wondering if there is an easy way to auto-mount local and network NTFS drives when ubuntu loads in 9.10, or does it still have to be entered manually in the fstab file?

---

### Post by nixscripter on 2009-11-28
You could do it through dbus and HAL if you wrote a custom handler program, but fstab seems much easier to me. What is the reason you want it dynamic, but not in fstab?

---

### Post by Matt26 on 2009-11-28
> **nixscripter said:**
> You could do it through dbus and HAL if you wrote a custom handler program, but fstab seems much easier to me. What is the reason you want it dynamic, but not in fstab?

personally, i think the process could be a bit simpler and easier- basically, having a GUI alternative that automates the process would be great.

---

### Post by nixscripter on 2009-11-29
If you just wanted a GUI, try pysdm:

[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

---

### Post by Matt26 on 2009-11-29
> **nixscripter said:**
> If you just wanted a GUI, try pysdm:

[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

thanks for the suggestion, i might try that out- any idea if this tool supports network NTFS drives as well?  i'm guessing by looking at the screen shots that it doesn't.

---

### Post by nixscripter on 2009-12-02
I'm not sure, but I bet if you could write an fstab entry for it, it could put it in.

---

