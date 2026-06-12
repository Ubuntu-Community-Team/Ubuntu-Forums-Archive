---
title: "VNC Frustration"
date: 2008-12-13
forum: Mythbuntu
---

### Post by sideslope on 2008-12-13
This should be really easy to do but I'm at a loss. I install Mythbuntu as a back end only because it will have no monitor or keyboard. 

I enable VNC and for set up, it works fine. I can remote to the gui and configure. BUT, when I disconnect the monitor, mouse, and keyboard, the #$%^ing VNC won't start. 

The box enters run level 2 and I can ssh no problem. But why in the hell won't VNC start? If it's backend only, it shouldn't want (or need) a monitor hooked up to it. 

Help me. This should work out of the box!

Thanks,

Slope!

---

### Post by SiHa on 2008-12-14
Perhaps your X server isn't starting because it can't find a video device? when you've ssh'ed in, have a look at **/var/log/X11/Xorg.0.log** for any clues. You might need to force it to ignore the autodetect, and just output to VGA regardless.
does ```
ps -A | grep Xorg
```return anything?

Just a thought, why not just leave a monitor connected, you could probably pick up an old 15" CRT for next to nothing. I guarantee there will come a day when you can't ssh or vnc, and you need to physically sit in front of that box.

---

### Post by sideslope on 2008-12-14
Thanks for the replay SiHa. I took a look at the log and you are correct. It sees no monitor and shuts down:

(II) Loading /usr/lib/xorg/modules/drivers//ch7017.so
(II) Module ch7017: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 4.1
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVODDC_D" removed.
(II) intel(0): Output VGA disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA disconnected
(WW) intel(0): Unable to find initial modes
(EE) intel(0): No valid modes.
(II) UnloadModule: "intel"
(II) UnloadModule: "ch7017"
(II) Unloading /usr/lib/xorg/modules/drivers//ch7017.so
(II) UnloadModule: "tfp410"
(II) Unloading /usr/lib/xorg/modules/drivers//tfp410.so
(II) UnloadModule: "ivch"
(II) Unloading /usr/lib/xorg/modules/drivers//ivch.so
(II) UnloadModule: "ch7xxx"
(II) Unloading /usr/lib/xorg/modules/drivers//ch7xxx.so
(II) UnloadModule: "sil164"
(II) Unloading /usr/lib/xorg/modules/drivers//sil164.so
(II) UnloadModule: "int10"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

And here is the result of the process command: user@MythTV:/var/log$ ps -A | grep Xorg
 5397 tty7     00:00:00 Xorg


So the answer to your question about just having a junk monitor is: I don't have the room. I have a server farm running and I use remote desktop to get to them. There isn't any room for a monitor so I would prefer not to add on to this box. 

So my next question is: How do I disable the check and force this to load anyway? There must be a setting somewhere. Please let me know what you think and thanks for the answer. 

Slope!

---

### Post by SiHa on 2008-12-14
Sorry - for Intel, I haven't a clue. The Nvidia drivers have an option called 'IgnoreEDID', which you can use to force the chipset to do what you tell it. I've  just done a quick google, and I don't think it's used in the Intel drivers.

Essentially, you need to ensure your Xorg.conf has a useable Montitor definition which will work **when** you someday need to connect one. The you need to tell it to use this monitor regardless of what it thinks is connected. You might want to post to the 'Hardware & laptops' forum, now that you know the problem.

PS - looks like the **ps -A | grep Xorg** was a red herring, I thought the X Server would quit if it couldn't find anything to display to, but it looks like I was wrong.

---

### Post by maxim99 on 2008-12-29
The intel driver version you're using doesn't allow for that functionality. It itself shuts the X server down when there is no connected device. You'll have to compile up the new driver version or use the alpha Jaunty.

---

