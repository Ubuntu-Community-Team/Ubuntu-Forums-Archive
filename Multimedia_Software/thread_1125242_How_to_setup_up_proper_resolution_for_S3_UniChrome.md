---
title: "How to setup up proper resolution for S3 UniChrome video card on Ubuntu 8.1"
date: 2009-04-14
forum: Multimedia Software
---

### Post by amylase on 2009-04-14
My computer is Shuttle XPC Barebone SK43G. This is my video card:
VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

I'm running Ubuntu 8.1. I already have "xserver-xorg-video-openchrome 1:0.2.903-0ubuntu3" installed, yet currently the highest resolution I have is 800x600. I have read various threads include these, without success. Please advise. Thanks very much.

[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

[https://www.linuxquestions.org/questions/linux-hardware-18/s3-unichrome-driver-361066/](https://www.linuxquestions.org/questions/linux-hardware-18/s3-unichrome-driver-361066/)

[http://www.linuxforums.org/forum/redhat-fedora-linux-help/124543-solved-fc9-display-problem-s3-unichrome.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/124543-solved-fc9-display-problem-s3-unichrome.html)

[http://www.openchrome.org/trac/wiki/Installation](http://www.openchrome.org/trac/wiki/Installation)

[https://launchpad.net/ubuntu/gutsy/i386/xserver-xorg-video-unichrome/1:0.2.6.99-0ubuntu1](https://launchpad.net/ubuntu/gutsy/i386/xserver-xorg-video-unichrome/1:0.2.6.99-0ubuntu1)

PS: one of the articles mentioned gksudo gedit /etc/X11/xorg.conf, looking for Device "vesa" and to change it to chrome. I do not see Device "vesa" in xorg.conf but added it in anyway. Still no difference to resolution... :(

---

### Post by iridium21 on 2010-05-12
Did you ever solve this problem because I have it too on 10.04 :(

---

