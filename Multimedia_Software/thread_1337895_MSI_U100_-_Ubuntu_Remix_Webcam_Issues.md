---
title: "MSI U100 - Ubuntu Remix Webcam Issues"
date: 2009-11-25
forum: Multimedia Software
---

### Post by mrunowich on 2009-11-25
Hi-

Just got my netbook today from newegg.com. Wiped of windows xp and installed ubuntu 9.10 netbook remix. I play guitar and my friends back home would like to see and hear me play, and unfortunately I cannot get the built in webcam to work. Fn+F6 does nothing. If ya got the solution or some advice plz post up. Thanks

---

### Post by BenAshton24 on 2009-11-25
What netbook is it?

---

### Post by mrunowich on 2009-11-26
MSI Wind U100

---

### Post by BenAshton24 on 2009-11-26
Here are some of the known issues, webcam support being one of them.

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#MSI%20Wind%20U100](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#MSI%20Wind%20U100)

Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435352](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435352)

There are a few workarounds in the replys on the bug report that look promising, however the easiest thing would be to downgrade to jaunty for a bit. Hopefully a solution will be found soon.

Ben.

---

### Post by mrunowich on 2009-11-29
Thanks, I know a little bit but bare with me, does this mean the kernel I currently have installed does not support the webcam installed?

---

### Post by Metteke on 2009-12-06
the webcam is supported in the kernel, but the video driver messes up the usb hub where the camera internally is connected to. Startup with the camera disabled should do the trick.
According to the bug status (see link above) a fix is released yesterday.
My question is: where can I get this fix?? Will it be in a new kernel?
Currently I run 2.6.31-16-generic...

thx,
Maarten

---

