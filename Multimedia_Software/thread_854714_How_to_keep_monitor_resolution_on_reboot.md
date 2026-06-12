---
title: "How to keep monitor resolution on reboot?"
date: 2008-07-09
forum: Multimedia Software
---

### Post by tubegeek on 2008-07-09
I use a Ubuntu 8.04 box for my media and I don't always have a monitor connected.

Howe can I get the machine to keep its screen resolution upon reboot?

When I reboot with no monitor connected, I get a generic monitor with 800x600 resolution and the openchrome driver. How can I get the setting for the monitor/driver to stick to the one that I get when I reboot WITH a monitor connected? (1600 x 1200, openchrome.)

---

### Post by Aenima99x on 2008-07-11
Same here.....anyone?

---

### Post by wolfen69 on 2008-07-11
try
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Aenima99x on 2008-07-11
> **wolfen69 said:**
> try
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Why would I want to overwrite my working xorg.conf? I've had enough trouble trying to get the ATI drivers working correctly and when I finally do, every time I reboot it doesn't detect my plasma correctly.

---

