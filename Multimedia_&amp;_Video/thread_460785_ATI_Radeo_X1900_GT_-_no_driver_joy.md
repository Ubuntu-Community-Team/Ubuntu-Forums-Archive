---
title: "ATI Radeo X1900 GT - no driver joy"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by negativ on 2007-06-01
PCIe Radeon X1900 GT

read EVERY. SINGLE. POST.  in this thread:

[http://ubuntuforums.org/showthread.php?t=221320](http://ubuntuforums.org/showthread.php?t=221320)

best result was a black screen where GDM should be.

reformatted, reinstalled numerous times.

Tried this:

[http://ubuntuforums.org/showthread.php?t=402937](http://ubuntuforums.org/showthread.php?t=402937)

Failed; [http://darcs.frugalware.org/repos/frugalware-current/source/x11-extra/fglrx/fglrx-2.6.20.patch](http://darcs.frugalware.org/repos/frugalware-current/source/x11-extra/fglrx/fglrx-2.6.20.patch) no longer exists.

No method here worked either:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Anyone got another idea?

---

### Post by eye208 on 2007-06-01
Try this:

1. Boot Feisty Live CD in safe graphics mode.
2. Use restricted drivers manager to install fglrx.
3. Press Ctrl-Alt-Backspace to restart X.
4. Enter "fglrxinfo" in a terminal.

The output of fglrxinfo should list ATI Technologies, the name of your card and OpenGL version 2.0.x with the driver version in brackets (8.34.8). If it does, then this is a working method for you to install the driver.

---

