---
title: "Help, I tried nVidia drivers and destroyed my Xserver"
date: 2006-07-23
forum: Multimedia &amp; Video
---

### Post by vinoloco on 2006-07-23
OK,

Here is the deal...

I have an older Nvidia card (RIVA TNT2) and tried to install the Nvidia drivers on my "Drake" system...

Now at reboot I get the dreaded "Failed to start X server..." notice

Can anyone help me fix this?  I don't want to/think I need to totally re-load my OS....

Anyway, here is the detail of my card when I issues an "lspci" command:

nVidia Corp. NV5M64 [RIVA TNT2 Model 64/Model 64 pro] (rev 15)


Thanks for the help...

vino

---

### Post by tseliot on 2006-07-23
boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "nv" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

The Xserver should work fine


After that you can install the **Legacy driver** by using **Method 1** of this guide of mine:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by vinoloco on 2006-07-23
Thanks!  Worked fine...

I think my original problem was that I wasn't installing the "legacy" support.

--  vino

---

