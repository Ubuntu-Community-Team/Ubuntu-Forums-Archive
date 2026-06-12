---
title: "ubuntu's vanilla builds of 2.6.31 are missing drivers/media modules"
date: 2009-08-16
forum: Multimedia Software
---

### Post by ameno on 2009-08-16
i upgraded to 2.6.31-rc6 mainly because of the prominent security bug(fix) in the network stack. i really like the vanilla builds, because they save me from compiling myself and work very well with the rest of ubuntu.
(if you have no idea what im talking about: [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds))

since the beginning of the 2.6.31 dev cycle the .config seems to be out of sync. therefore some modules are not built (maybe there are other culprits as well), namely the modules under kernel/drivers/media/.
(can be verified for installed packages with: ```
dpkg -L linux-image-<version> | grep drivers/media
```
if it does not return any matches, they are missing)

i noticed this because there was no /dev/video0 for my tv card, because the bttv module was not loaded. im idling in the kernel irc channel to notify them. just wanted to document this for google and you ;)

---

