---
title: "How to enable the compiz-like effects on Ubuntu 12.04"
date: 2013-05-24
forum: Multimedia Software
---

### Post by MEPHIST0FELIZ on 2013-05-24
Hello everyone.

I would like to know how can I enable the compiz-like effects on ubuntu 12.04. I assume I have a problem because I can't change the launcher's icons size either, I don't see the slider on the appearance section of system settings.

I'm running Ubuntu 12.04 on an HP dv-5 laptop with this hardware:

[I]Microprocessor 2.40GHz Intel Core i5-450M Processor with Turbo
Boost Technology
Memory 4 GB DDR3 DIMM[/I]
*Video Graphics Intel HD Graphics with up to 1696MB total graphics*

Just for the record, when installing ubuntu, I had to use the nomodeset option at boot because if I didn't the desktop wouldn't show up and the screen stayed black.

Any help would be greatly appreciated.

Kasim.

---

### Post by hansdown on 2013-05-24
Hi 
MEPHIST0FELIZ.

You need to install 

> compizconfig-settings-manager

---

### Post by MEPHIST0FELIZ on 2013-05-25
Hi hansdown!

Thank you for your support.

I installed compizconfig-settings-manager as you said, but I can't find the compiz section in system settings nor in the upper-right corner of the desktop.

What should I do now?

---

### Post by hansdown on 2013-05-25
If you're using unity, type

> ccsm

It should show up.

---

### Post by MEPHIST0FELIZ on 2013-05-31
I opened the compiz configuration settings manager and I activated the wobbly windows but they don't wobble. What can I do?

---

### Post by hansdown on 2013-05-31
This tutorial will explain it better than I can

[http://www.howtoforge.com/install-compiz-on-the-unity-desktop-on-ubuntu-12.04-precise-pangolin](http://www.howtoforge.com/install-compiz-on-the-unity-desktop-on-ubuntu-12.04-precise-pangolin)

Don't forget the

> unity --reset

command.

---

