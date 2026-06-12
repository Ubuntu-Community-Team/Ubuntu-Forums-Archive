---
title: "NVIDIA &amp; boot up"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by ags40 on 2008-02-28
NVIDIA 6200. Every time I enable the video driver, when I start my computer, I have to reboot twice. Is there a way around this? Thanks everybody,

---

### Post by overdrank on 2008-02-28
> **ags40 said:**
> NVIDIA 6200. Every time I enable the video driver, when I start my computer, I have to reboot twice. Is there a way around this? Thanks everybody,

HI and have you tried to reconfigure your xorg?

---

### Post by ags40 on 2008-02-29
How could I do That?

---

### Post by overdrank on 2008-02-29
> **ags40 said:**
> How could I do That?

Ok you can use the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
In the terminal located under applications, accessories

---

### Post by ags40 on 2008-02-29
Thanks overdrank. I just tried your sugestion. Will see what happens as the day goes by.  By the way, what does it do: sudo dpkg-reconfigure -phigh xserver-xorg?
thx again.

---

