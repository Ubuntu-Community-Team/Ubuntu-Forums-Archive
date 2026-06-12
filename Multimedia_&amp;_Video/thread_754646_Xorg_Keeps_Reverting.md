---
title: "Xorg Keeps Reverting"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by absolution87 on 2008-04-14
Hi,

Im running ubuntu 7.10. I just installed the nvidia 8800gt drivers direct from the nvidia site, it sets up the xorg and everything runs fine, then i reboot, and ill the settings revert and i have vesa drivers and a low resolution. i dont know what im doing wrong. any help is appreciated

Thanks

---

### Post by erginemr on 2008-04-14
Normally I would suggest you to stick to the NVidia driver provided by Ubuntu's restricted drivers manager. But now that you are already in the binary driver business, I suggest you to download ENVY from:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

and let it install and configure the correct driver for your card.

---

### Post by pbhj on 2008-04-14
> **absolution87 said:**
>  it sets up the xorg and everything runs fine, then i reboot, and ill the settings revert and i have vesa drivers and a low resolution

I had a similar problem that I fixed by setting the xorg.conf file to be read only.

```
chmod a-w /etc/X11/xorg.conf
```

---

