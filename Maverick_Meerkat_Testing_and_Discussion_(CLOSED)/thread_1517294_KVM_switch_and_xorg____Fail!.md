---
title: "KVM switch and xorg    Fail!"
date: 2010-06-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by robert shearer on 2010-06-24
I am using one monitor(CRT),keyboard and mouse on two compys via a (ps2) KVM switch.


Pre Karmic it was a simple matter of editing xorg.conf to set the monitors vsync and horizontal refresh to get proper resolution and refresh rate.

Now with dynamic Xsetting at each boot the kvm switch is seen first and, at best, I get the right resolution but always 60Hz instead of 85Hz refresh.
 
Ouch my eyes !!!!!

Post Karmic I had to first plug the monitor direct to each compy and run ```
Xorg -configure
``` etc to provide the xorg file and edit as above.

Now in Meervrick Mugrat  Xorg -configure seems to be broken and aborts with a comment about 'number of screens not matching number of instances'

Any suggestions gratefully received...

Would like to continue with Ubuntu though this is a show-stopper for me.

Generally user configuration options seem to have been getting less with each new release. :confused: or is it just me ??

**Edit...** Ok, I managed to generate an xorg.conf file and edit it for my monitor.
Moved it to /etc/X11/xorg.conf  as /
Reboot and .... **no change**.

I thought an xorg.conf if present had priority over auto-detection so something is well amiss.

As this method worked for previous releases and the only thing to have changed is Moovrock Mangoat then presumably it is a bug ??

comments ??

---

### Post by dino99 on 2010-06-25
yes you might report these issues (already seen other users with crt problems, i think its a linux trouble as it directly deal with X now)

---

### Post by robert shearer on 2010-06-25
> i think its a linux trouble as it directly deal with X now

Well, it is dealing with X better than ever before because it sets the resolution correctly now.
Previously I only got 800x600 before configuration and now I get 1024x768.

Unfortunately it seems to default to 60Hz refresh rate for LCD screens and there is **no way** to alter this for CRTs.

From this link...
[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)
It appears that sections such as monitor settings can be put in /usr/share/X11/xorg.conf.d and be loaded before autodetect.

> Files ending in *.conf in the /usr/lib/X11/xorg.conf.d/ directory (NOTE: will be changed to /usr/share/X11/xorg.conf.d for 10.10) are automatically loaded by X at start prior to reading the xorg.conf. These files can each contain one or more Sections in the same format used by xorg.conf. 

However I have tried that and nothing changes. :confused:

---

