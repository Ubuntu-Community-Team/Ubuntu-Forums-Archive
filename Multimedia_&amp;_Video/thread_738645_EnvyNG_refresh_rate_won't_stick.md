---
title: "EnvyNG refresh rate won't stick"
date: 2008-03-28
forum: Multimedia &amp; Video
---

### Post by luceerose on 2008-03-28
Installed nvidia drivers via EnvyNG.
The nvidia settings keep putting the refresh rate on 87hz interlaced (which looks like crap)
I want it set on 85hz.
When I go to nvidia settings and change it, all is good... That is until I restart X or reboot, then it's back to 87 interlaced.

Running Kubuntu Hardy.

Anyone got any ideas?

---

### Post by wolfen69 on 2008-03-28
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by luceerose on 2008-03-28
> **wolfen69 said:**
> ```
sudo dpkg-reconfigure xserver-xorg
```

That just puts everything back to defaults & disables the nvidia restricted driver.

---

