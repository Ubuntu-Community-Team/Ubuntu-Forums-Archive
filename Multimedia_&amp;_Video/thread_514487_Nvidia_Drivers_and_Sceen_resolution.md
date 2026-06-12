---
title: "Nvidia Drivers and Sceen resolution"
date: 2007-07-31
forum: Multimedia &amp; Video
---

### Post by SniperClops on 2007-07-31
Greetings,

I installed the Nvidia drivers and can only have 800x600 resolution. When I run "sudo nvidia-settings" I still can't change the resolution. What do I have to do to get my resolution to 1024x768 or 1152x864 and change the refresh rate, it is stuck at 60?

---

### Post by dreadlord_chris on 2007-07-31
> **SniperClops said:**
> Greetings,

I installed the Nvidia drivers and can only have 800x600 resolution. When I run "sudo nvidia-settings" I still can't change the resolution. What do I have to do to get my resolution to 1024x768 or 1152x864 and change the refresh rate, it is stuck at 60?

Which NVIDIA card are you using, and post the contents of **/etc/X11/xorg.conf**

---

### Post by wolfen69 on 2007-08-01
try:
```
sudo dpkg-reconfigure xserver-xorg
```

---

