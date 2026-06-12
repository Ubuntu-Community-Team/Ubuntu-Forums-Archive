---
title: "7600GS can't user driver, please help."
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by erv2 on 2007-10-22
hello all,

i just installed Gusty using the alternative CD. but after the ubuntu progress bar, one of my screen goes "out of range" the other one displays random strange stripes. i am able to login and enter the password, but the graphics is all wrong.

then i tried to boot into recovery mode and run:

```

sudo dpkg-reconfigure xserver-xorg

```

it can detect my 7600GS and so as one of my screen on analog, when i finish all the setting and start with normal mode, it goes to some setup screen asking me to set the screen resolution, also from the Driver section, my driver is VESA instead of nvidia.

so what do i do now to get ubuntu to use the correct driver and screen not "out of range"???

i m new to ubuntu, i m getting quite frustrated at the moment/ please help me.

---

### Post by overdrank on 2007-10-23
> **erv2 said:**
> hello all,

i just installed Gusty using the alternative CD. but after the ubuntu progress bar, one of my screen goes "out of range" the other one displays random strange stripes. i am able to login and enter the password, but the graphics is all wrong.

then i tried to boot into recovery mode and run:

```

sudo dpkg-reconfigure xserver-xorg

```

it can detect my 7600GS and so as one of my screen on analog, when i finish all the setting and start with normal mode, it goes to some setup screen asking me to set the screen resolution, also from the Driver section, my driver is VESA instead of nvidia.

so what do i do now to get ubuntu to use the correct driver and screen not "out of range"???

i m new to ubuntu, i m getting quite frustrated at the moment/ please help me.

Hi, lets try the command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And hopefully this will get you to the desktop then you can go from there. Also I have not tried the dual monitors but it may help to disconnect one and get to the desktop to install the correct drivers. Hope this helps and good luck!

---

