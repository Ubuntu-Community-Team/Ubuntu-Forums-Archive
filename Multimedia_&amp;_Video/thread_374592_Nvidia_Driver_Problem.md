---
title: "Nvidia Driver Problem"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by pt123 on 2007-03-02
I have an nvidia A6600GT card.

When I an using the non-nvidia drivers its all fine. But when I installed the nvidia drivers xorg crashes on boot up.

Attached is the Xorg.0.log which is zipped and also an Xorg.0.log.old file which contains

```

(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

Can someone please look at it and help me out as to what is the problem.

---

### Post by pt123 on 2007-03-02
Bump

Anyone?

---

### Post by rsambuca on 2007-03-03
What method did you use to install the driver?

---

### Post by pt123 on 2007-03-03
The one here
[http://easylinux.info/wiki/Ubuntu_Edgy](http://easylinux.info/wiki/Ubuntu_Edgy)

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig

It is strange it used to work sometime back (1 or two years).

But after the fatal and well publicised xorg botched update (6 months back?) it would screw up like sometimes when I booted up with xorgs BSOD.

But now its happening everytime.

---

### Post by CrazyTn on 2007-03-03
I used the envy script to install my video card driver.

here is the link.

[http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

I am a newbie so don't rely too much on my advice

---

### Post by pt123 on 2007-03-03
^ Thanks that was awesome worked like a charm, it even detected my monitor.

Not sure why the new drivers aren't in the repository.

Since you seem to know the right places, do you know whats the best way to install Beryl on the desktop

Thanks

---

### Post by rsambuca on 2007-03-03
You should let us know in your profile what version of ubuntu you are using.  But if you are using Edgy, the best instructions are [[COLOR="Red"]here.[/COLOR]]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia")

---

