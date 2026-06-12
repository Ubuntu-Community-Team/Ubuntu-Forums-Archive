---
title: "Installing XFX One (Radeon HD 5450)"
date: 2013-03-04
forum: Multimedia Software
---

### Post by NekoCahlan on 2013-03-04
Hello everyone!

I have recently decided to dive into the Linux scene. This being said, I'm already having problems right from the start! >_<

After the initial installation of 12.10 32bit Ubuntu, everything seemed very slow and laggy. I looked at System Settings > Details, and my GPU showed as "Unknown". Well that's not cool...

I went to the AMD website, and downloaded their 13.1 Linux driver, which to my dismay was a .run file. Being new to linux, I had no idea what to do with this file. 

I found the unofficial guide here: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide)

I attempted to install via instructions labeled "Using Ubuntu-supplied fglrx/Catalyst" and rebooted. Now my GPU shows as "VESA: CEDAR"

This is driving me crazy, please help someone! Thanks >_<

---

### Post by QIII on 2013-03-04
Hello and welcome!

That is a reporting irregularity.  "Cedar" is ATI's code name for the series of GPUs in that line, so that is to be expected.

If you would, please post back the results of the following command in the terminal:

```
fglrxinfo
```

---

### Post by Bucky Ball on 2013-03-04
*Thread moved to **Multimedia & Video***

---

### Post by NekoCahlan on 2013-03-04
Thanks for moving this to the correct place!

Anyway, here are the results!

> display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 5450
OpenGL version string: 4.2.11903 Compatibility Profile Context


---

### Post by QIII on 2013-03-04
That indicates that the driver is installed and working.

Would you please try to open the Catalyst Control Center

```
gksudo amdcccle
```

and tell me if it opens?

---

### Post by NekoCahlan on 2013-03-04
It asked me for my password, but opened afterwords. It appears to work, but I have a hard time believing that a 5450 cannot play fullscreen 720P videos on youtube. Something is fishy... Even being a media card, it should be able to do just that, play media. :(

---

### Post by NekoCahlan on 2013-03-04
Are the drivers garbage, or...?

---

### Post by QIII on 2013-03-04
That can be disheartening, but that likely has nothing to do with either your card or Ubuntu.

If it's full screen Flash content, that often presents difficulty in the Linux world.  Adobe pulled Linux development support for Flash and will only be providing security updates for about the next four years.

---

### Post by NekoCahlan on 2013-03-04
Oh... Well that makes me feel slightly better.

However I just noticed that my sound doesn't work...

This old HP workstation has some onboard Realtek sound chip. How would I go about finding the drivers for that?

Also, my 5450 has HDMI, so if I could get that audio working, I'd be fine with that too. Either one really! Thanks!

---

