---
title: "speeding up internet connection in ubuntu"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by sulekha on 2009-09-24
Hi all,
I got the following tip from pcmech site

**speeding up internet connection in ubuntu**
you can speed up internet connection by disabling IPV6(iff it is not needed)

sudo gedit /etc/modeprobe.d/aliases

edit the line alias net-pf-10 ipv6 as alias net-pf-10 off

then save & reboot

will this tip increase the net speed substantially in ubuntu ??

---

### Post by kerry_s on 2009-09-24
no, that don't work no more. ipv6 is in the kernel now. you can disable it in the browser "about: config" setting though.

---

### Post by scorp123 on 2009-09-24
> **kerry_s said:**
>  disable it in the browser "about: config" setting though. +1 on that one ...

Off-topic question: How did you set the "WTF" in your avatar? :D  I like that one :) (it's better than the standaed "extra creamy topping something bla bla" or "gee those aren't roasted" .... :D  ) ... So how did you set that? (Sorry for going OT .... )

---

### Post by wojox on 2009-09-24
Edit the file:

```
gksudo gedit /etc/modprobe.d/blacklist
```

and add the line:
```
blacklist ipv6
```

then reboot. This removes IPv6 from the kernel entirely, not just the browser.

---

### Post by kerry_s on 2009-09-24
that don't work to, it's a kernel bug, you would have to recompile the kernel to disable ipv6.

> Off-topic question: How did you set the "WTF" in your avatar?

in your user cp, under "edit your details"-> custom user title

---

### Post by scorp123 on 2009-09-24
> **kerry_s said:**
> that don't work to, it's a kernel bug, you would have to recompile the kernel to disable ipv6. You are misinformed. It does work. Without recompiling. If you "blacklist" the ipv6 module it will not be loaded ... which might on some systems indeed increase the performance of ipv4 a little bit.

---

### Post by scorp123 on 2009-09-24
> **wojox said:**
>  Edit the file:
```
gksudo gedit /etc/modprobe.d/blacklist
``` 

Small typo there .... the correct file would be:
**/etc/modprobe.d/blacklist.conf**

---

