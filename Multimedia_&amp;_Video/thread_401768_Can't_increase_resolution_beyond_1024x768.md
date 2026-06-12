---
title: "Can't increase resolution beyond 1024x768"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by encynerate on 2007-04-05
So I've gotten my shiny geforce 7600GT PCI-E card all nice and installed, had no problems installing the drivers what-so-ever, but I've seen to hit a minor snag. But I can't seem to increase my screen resolution beyond 1024x768. There just is no option in the screen resolution system tool, or the nVidia driver too. I tried changing my xorg, my optimal resolution is 1280x1024, to change to the resolution manually, but I always somehow manage to screw it up. (thank god for backups). Anybody have an idea of what I can do to fix this? And would posting my XORG be helpful at all?

edit: also, I'm not sure if my monitor has anything to do with it, 1280x1024 is the max it can support and had no trouble whilst running XP Pro.

---

### Post by RaZer0r on 2007-04-05
did you try to reconfigure your xorg config with the tool?
```

sudo dpkg-reconfigure xserver-xorg

```
it worked in my case... or you can try to add the screen resolutions manually to your xorg.conf
(in /etc/X11/xorg.conf)

---

