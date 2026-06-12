---
title: "devede in ubuntu 13.04"
date: 2013-08-27
forum: Multimedia Software
---

### Post by m3t3ors on 2013-08-27
i use devede to create my dvds but when i installed devede on 13.04 its not working right?
when i add my movie files and select desktop to save my finished file i cant press OK
its not highlighted, only option is cancel
is this a bug somewhere or is there a fix for it

---

### Post by Yellow Pasque on 2013-08-28
I think it's a bug. I installed devede in my saucy VM, and it's set to use ffmpeg to encode by default (Ubuntu now uses avconv). So either devede should shuold depend on ffmpeg or the default encoding setting should use avconv.

Try either:
1) Install ffmpeg package
2) In devede's settings, you can change it to use avconv for encoding

Option 2 would be preferred.


EDIT: I already had ffmpeg installed in the VM, so maybe that's not the default setting..

---

