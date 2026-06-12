---
title: "Linux 686 and ATi driver issues?"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by evil_elman on 2006-07-11
I just jumped to the 686 kernel (installed through Synaptics). Everything works fine (it seems a bit wiffier) but the graphics are really weird now for some reason:

* Video playback is now jerky
* Buttons and controls are slow to react
* I type faster than the letters appear
* Windows are slower to minimize and maximize (the animation)

and so on.

Terminal outputs are all the same as before (No MESA, I've got direct rendering and it reports the driver version correctly) so I don't see where the issue is.

I've tried reconfigure the Xorg, re-install the ATi (fglrx) driver and so on, but it's still the same.

Am I doomed to live with a 386 kernel here?

---

### Post by Dubbayoo on 2006-07-11
I haven't noticed any of those issues with a Radeon 8500

---

### Post by evil_elman on 2006-07-11
Hmmm... Weird...

Btw... I'm using a Mobility Radeon X600 (64MB).

I just installed a heap of updates through Synaptics now... Let's see if it made a difference... *Hopes*

---

### Post by tseliot on 2006-07-11
if you installed the ATI driver from the repos make sure you have installed the restricted modules for your kernel:
```
sudo apt-get install linux-686
```

---

### Post by matthew on 2006-07-11
I'm having no problems whatsoever. The kernel and ati drivers are coexisting well on my machine.

```
matt@telecaster:~$ uname -a
Linux telecaster 2.6.15-26-686 #1 SMP PREEMPT Fri Jul 7 19:48:22 UTC 2006 i686 GNU/Linux
matt@telecaster:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

---

### Post by evil_elman on 2006-07-11
> **tseliot said:**
> if you installed the ATI driver from the repos make sure you have installed the restricted modules for your kernel:
```
sudo apt-get install linux-686
```

Do I have to do anything else than this and restart X?

Nothing happened when I ran the above command. Everything already installed according to the output.

My driver is 8.25.18

I can also mention that the fading (for when you shut down or when you enter administrator password) is also fading quite a lot slower than before.

I also took the libery to remove all the old kernels (after all these updates) but with no result...

---

### Post by tseliot on 2006-07-11
> **evil_elman said:**
> Do I have to do anything else than this and restart X?

Nothing happened when I ran the above command. Everything already installed according to the output.

My driver is 8.25.18

I can also mention that the fading (for when you shut down or when you enter administrator password) is also fading quite a lot slower than before.

I also took the libery to remove all the old kernels (after all these updates) but with no result...
I wouldn't know (I don't use ATI cards).

Maybe you could try reinstalling the driver

---

### Post by evil_elman on 2006-07-11
I did try that (uninstalled from Synaptics), used VESA for one boot to make sure it worked and re-installed it to no avail...

However, I think it's not due to the video driver. I think there's actually something wrong with the laptop in some other area.

Anyhow... I'll stick with 386 for now. It even boots faster than with 686 kernel for some reason... And it's also otherwise problem-free...

---

