---
title: "mythfrontend crashes my X session"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by tranquillion on 2007-04-25
Hi,

I just did a fresh install of Feisty and MythTV, following the official installation instructions at [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV).  MythTV is running mostly fine, but with one severe problem: everytime I quit mythfrontend, my X session crashes! Note that watching TV and recording works fine, only when exiting mythfrontend, X dies, which gets a little annoying...

Is this happening to anybody else? Unfortunately I don't quite know where to start looking... I didn't see anything suspicios in /var/messages or ~/.xsession-errors. /var/log/Xorg.0.log.old shows the following:

```
<snip>
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/lib/xorg/modules/extensions//libGLcore.so(XMesaResizeBuffers+0x29) [0xae96bd29]
3: /usr/lib/xorg/modules/extensions//libGLcore.so [0xae968900]
4: /usr/lib/xorg/modules/extensions//libglx.so [0xb7b9094a]
5: /usr/bin/X(compPositionWindow+0x59) [0x80f6039]
6: /usr/bin/X(ReparentWindow+0x1a7) [0x807a8a7]
7: /usr/bin/X(ProcReparentWindow+0xd5) [0x808c055]
8: /usr/bin/X [0x8142531]
9: /usr/bin/X(Dispatch+0x19f) [0x808c61f]
10: /usr/bin/X(main+0x495) [0x8074785]
11: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d21ebc]
12: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11.  Server aborting
```

(I'm running Feisty on a P4 with a NVidia FX5200 card, using the standard (non-proprietary) drivers.

I'd be grateful for any pointers!

Thanks
Klaus

---

### Post by FluffyElmo on 2007-04-25
You might want to try the proprietary drivers, I've been using Myth with Nvidia hardware for a while with no problems. You should be able to find the Myth log files in */var/log/mythtv/*,* /var/log/mythtv/mythfrontend.log* may give some additional information.

---

### Post by superm1 on 2007-04-25
I would second installing the proprietary drivers in this instance.  (System->Administration->Restricted Drivers to turn them on)

---

### Post by tranquillion on 2007-04-26
The problem is that I was never able to get the proprietary drivers to display the right screen resolution. (I have a FX5200 and a 1920x1200 LCD monitor). I've read in the past that the proprietary drivers don't play nice with the FX5200 at high resolutions, and from my experience this seems to be indeed the case (I've tried *sudo dpkg-reconfiure xserver-xorg* and experimented with a lot of settings, but to no avail...)

Anyways, I switched to the proprietary drivers, and it crashes no more... I guess I just have to live with a non-native screen resolution for now... it doesn't make a difference when watching TV ;)

Thanks
Klaus

---

### Post by superm1 on 2007-04-26
> **tranquillion said:**
> The problem is that I was never able to get the proprietary drivers to display the right screen resolution. (I have a FX5200 and a 1920x1200 LCD monitor). I've read in the past that the proprietary drivers don't play nice with the FX5200 at high resolutions, and from my experience this seems to be indeed the case (I've tried *sudo dpkg-reconfiure xserver-xorg* and experimented with a lot of settings, but to no avail...)

Anyways, I switched to the proprietary drivers, and it crashes no more... I guess I just have to live with a non-native screen resolution for now... it doesn't make a difference when watching TV ;)

Thanks
Klaus
Klaus,

With the proprietary drivers, look into disabling the EDID for your monitor and using a modeline instead.  Might be able to get higher resolutions.

---

### Post by FluffyElmo on 2007-04-27
I have a Nvidia 7600GT and had a hard time getting native resolution to work with one of my LCDs. Not all LCd panels seem to report their configuration options correctly and there are a number of lightly documented options that you can put in your xorg.conf that can help, the readme and Google are your friend. In my case the following lines added to the Device section did the trick and might help you as well:

```
    Option "ExactModeTimingsDVI"
    Option "ModeValidation" "NoDFPNativeResolutionCheck"
```

I also have the following line in the relevant screen section, but it may not be necessary. I also have the regular 'Modes' lines as well and I'm not sure which takes precedence.
```
    Option         "metamodes" "DFP: 1440x900_75 +0+0"
```

In any case, odds are that you can get it working with some experimentation, Good Luck!

---

