---
title: "Fiesty Myth on an Epia MII 10000"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by jakev383 on 2007-05-11
I've installed Myth using this how-to:
[https://help.ubuntu.com/community/MythTV_Feisty](https://help.ubuntu.com/community/MythTV_Feisty)
And everything seems to install correctly. I'm running MythDora 4 on the backend.
When I setup FeistyMyth to connect to the backend and try and watch TV it gets jumpy. Like 2-3 frames per second. It's not the machine since I installed MythDora on that machine as well and am able watch TV normally.
Has anyone else run into a similar issue and can offer some help?
Thanks.

---

### Post by jakev383 on 2007-05-12
For those also searching.... The via video driver was not enabled by default - the vesa driver was. I did a:
sudo dpkg-reconfigure xserver-xorg
and made sure to select the via video driver and all was well after that.
Enjoy!

---

