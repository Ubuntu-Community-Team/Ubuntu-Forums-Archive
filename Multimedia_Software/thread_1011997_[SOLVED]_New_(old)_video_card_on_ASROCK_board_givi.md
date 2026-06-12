---
title: "[SOLVED] New (old) video card on ASROCK board giving me problems"
date: 2008-12-15
forum: Multimedia Software
---

### Post by r3bol on 2008-12-15
I have this fairly old motherboard: [http://www.asrock.com/mb/overview.asp?Model=K7VM2](http://www.asrock.com/mb/overview.asp?Model=K7VM2)
and I've been running my Ubuntu distro with its featured on-board graphics for a long time. A friend of mine has given me an old ATI card...
$: lspci | grep VGA 
01:00.0 VGA compatible controller ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
But I'm having problems booting with it sometimes. 

To get my card working I went into the bios and selected the AGP setting in something like Primary video device. Sometimes when I boot (this normally happens right after the load bar has reached the end - just before the log in screen), my monitor goes to sleep and doesn't wake up :) Sometimes it boots nicely. 

Has anyone an idea what could be happening or has had anything similar happen to them or could offer me advice?

Thanks.

---

### Post by r3bol on 2008-12-16
I'm having trouble reproducing this bug. Marking as solved. It may have been some teething problems, if there is such a thing.

---

