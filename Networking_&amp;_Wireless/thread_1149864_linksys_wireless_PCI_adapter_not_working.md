---
title: "linksys wireless PCI adapter not working?"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by Family-Users on 2009-05-05
how can I get this linksys wireless PCI adapter to work on ubuntu 10.8?
this is it right here  [http://www-id.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=ID%2FLayout&cid=1166859909276&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0927609276N09](http://www-id.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=ID%2FLayout&cid=1166859909276&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0927609276N09)

we don't have the CD for it anymore is there a way to get it working?

---

### Post by chili555 on 2009-05-05
There are several versions of this card. Let's ask the computer which one you have. Please open a terminal (Applications -> Accessories -> Terminal) and enter:```
sudo lshw -[SIZE="4"]C[/SIZE] network
```It will report both your wired and wireless data. Post it all and we'll go from there.

---

