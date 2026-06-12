---
title: "Resolution settings not saved"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by Andos on 2007-11-12
I'm running Ubuntu 7.10 on a Dell Inspiron 1520 with an Nvidia 8600M GT video card.  I have the nvidia drivers installed. The native resolution of my screen is 1440 x 900.  Gnome ran in this resolution fine after I installed ubuntu but recently it has stopped saving my settings.

Now when I boot up, it boots in 1024 x 768.  I have tried changing this in the system/administation/screens and graphics util and the nvidia-settings utility.  This works, but whenever i reboot or restart X  it reverts to 1024 x 768.  I reconfigured X to only use 1440 x 900 but gnome/X seems to be ignoring this.  Can anyone help?

---

### Post by Andos on 2007-11-24
Anyone got any ideas? I still haven't worked it out.

---

### Post by DFreeze on 2007-12-02
I'm having a similar issue. Native resolution also 1440x900, and trying to get a second monitor working, my laptop screen is suddenly set to 1024x768. Now I can go to Screens and Graphics in the menu, but selecting a generic LCD with 1440x900 gives me resolution options of 1024x768 max. How stupid is that!

So, sorry I can 't help you out, but I thought I'd put my story here as well, so yours is bumped back up. Hope to get some assistance soon (two weeks is way too much).

::EDIT::

I tried this command in my terminal
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

And I got my 1440x900 back. I'm not sure if it will last a reboot, but maybe it's of some help to you. Good luck!

---

### Post by Andos on 2007-12-02
I fixed this eventually!  I set the screen as a generic LCD 1440 x 900, then I went into the resolution settings in the preferences menu and set the resolution to 1440 x 900 in there as well.  That seemed to force it to save and it has been ok since!

---

