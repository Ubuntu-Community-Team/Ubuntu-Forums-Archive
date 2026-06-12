---
title: "HDMI connection - restart X server"
date: 2012-04-30
forum: Multimedia Software
---

### Post by agobaro on 2012-04-30
Hello,
I got a question about how Ubuntu handle an external monitor which is connected through HDMI.

I got a laptop (Ubuntu 12.04 and proprietary Nvidia drivers) with an HDMI output always connected to an external TV/monitor : all works fine (audio and video are routed properly to the external monitor using NVIDIA X Server Setting tool).

I noticed that when I turn ON or OFF the external TV/monitor , X server is suddendly restarted and so an unexpected closure of my working session can occur.

There is some way to modify this behaviour?
Thanks,

---

### Post by papibe on 2012-04-30
Hi agobaro. Welcome to the forums!

Usually going from and to 'Separate X Screens' requires restart.

Are you setting your monitors as separate X screens?

Regards.

---

### Post by agobaro on 2012-04-30
Hi papibe, thank you!

When the external monitor is turned off, 'Separate X Screens (requires X restart)' is the only choice available into NVIDIA X Server Settings (and there is only the laptop monitor available).

When the external monitor/TV is turned on (and so after an automatic X restart) , I can select the external monitor , choose “TwinView” and apply it (so to clone my laptop display on the external monitor).

If I turn off the external monitor, an automatic X restart occurs, and  NVIDIA X Server Settings tool returns to previous configuration where only laptop screen is available and 'Separate X Screens (requires X restart)' is the only choice a available.

Thanks,

---

### Post by BicyclerBoy on 2012-04-30
Dynamic twinview configuration with metamodes can help with one or more monitors being removed from a twinview setup..
Unfortunately this has to be cooked up in the /etc/X11/xorg.conf file.

Using X server you can switch between available modes..One of these modes can be a twinview with one real screen.
Internally the nVidia X server uses metamodes for one screen setups..

See chapter 13. of driver readme:
an example 2 ext twinview screens..VGA screen is disabled in video mode switch..
```

#/etc/X11/xorg.conf
Option "MetaModes" "CRT-0: 1600x1200,  DFP-0: 1024x768; NULL, DFP-0: 1024x768"

```
then use hot keys or xrandr to switch modes to one screen & then unplug it..

Or use xrandr to do all this is a script linked to a hot-key sequence..

---

### Post by agobaro on 2012-05-01
I tried to configure my xorg.conf following your suggestions and documentation available here :

[http://us.download.nvidia.com/XFree86/Linux-x86/295.33/README/configtwinview.html]("http://us.download.nvidia.com/XFree86/Linux-x86/295.33/README/configtwinview.html")

Now, even if the external monitor is turned off, I can see two monitors available into NVIDIA X server settings, and twinview is selected , instead of previous 'Separate X Screens (requires X restart)'.

But this doesn't seem to have changed the previously described behaviour (when I turn ON the external monitor , an automatic X server restart occurs).
I have a little experience with Ubuntu, but this seems to be some kind of autodetection which is working on HDMI port. 
Thanks,

---

### Post by BicyclerBoy on 2012-05-01
Yes you may be right..
Plugging in the HDMI monitor does cause hot-plug events..

Could this automatic restart be a X server/driver crashing?

You could look into the Xorg log files..
/var/log/Xorg.0.log & Xorg.0.log.old

---

### Post by agobaro on 2012-05-01
Thanks BicyclerBoy, you are right.
These are messages generated into Xorg.0.log when I turn off the external monitor:

```
Backtrace:
[ 24004.822] 0: /usr/bin/X (xorg_backtrace+0x37) [0xb771a627]
[ 24004.822] 1: /usr/bin/X (0xb7592000+0x18c3aa) [0xb771e3aa]
[ 24004.822] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb756f40c]
[ 24004.822] 3: /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so (0xb47f3000+0x63fe4) [0xb4856fe4]
[ 24004.822] Segmentation fault at address 0x38
[ 24004.822] 
Caught signal 11 (Segmentation fault). Server aborting
[ 24004.822] 
```

In the next few days, i will make some other tests trying different Nvidia driver.
Regards,

---

### Post by papibe on 2012-05-01
Take a look at post #2 of this [thread]("http://ubuntuforums.org/showthread.php?t=1967201&highlight=nvidia+ppa") to upgrade your driver as smooth as possible.

Regards.

---

### Post by agobaro on 2012-05-19
I'm sorry for this late update.
After I have updated Nvidia driver as suggested into previous post, this problem is not occuring anymore: now I'm using Nvidia driver 295.53 available into ubuntu-x-swat ppa.

Many thanks for your help!

---

