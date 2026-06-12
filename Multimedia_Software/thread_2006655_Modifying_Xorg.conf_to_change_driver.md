---
title: "Modifying Xorg.conf to change driver?"
date: 2012-06-19
forum: Multimedia Software
---

### Post by Agent_Riot on 2012-06-19
Simple question, related to my question in "Other Distros", but this one affects Ubuntu. I've heard some people with Intel Integrated drivers (I have a 960/965) have issues running VESA drivers, and they change the Xorg.conf to specify the correct Intel drivers. I believe this is my issue as I get a black screen and cursor only upon login. So i'm planning on trying that, but I need to know what the filename for the intel driver is and if I need to put it in a specific folder to use it.
I don't believe the driver will differ by distro, but if so i'll look it up that way.
 
Thanks for the info,

---

### Post by BicyclerBoy on 2012-06-19
First read/post the Xorg log file
"/var/log/Xorg.0.log"

It is as simple as putting
```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
#        Option          "AccelMethod" "EXA"
EndSection

```
in the "/etc/X11/xorg.conf" file.
This file might not exist by default but
Xorg -configure 
will create one..

The actual driver is called i915.
Check log file or run lsmod

But first check your log file.
The intel device requires kernel mode setting so remove any "nomodeset" from grub cmd..

---

### Post by Agent_Riot on 2012-06-19
Well I changed the xorg.conf file's driver "vesa" to "intel", then rebooted and now it states in system info and in lsmod that's it's using the 915. 

However now I don't think that's the issue. Upon trying to boot back up I get a black screen with a cursor still. No taksbar, icons, etc... Clicking does nothing. I can still ctrl-alt-f1 to reach a terminal though. But no window manager loads.

is Xclients a real file? and if so, is it someone that you can modify like the one I just did? Or am I better leaving it alone and running some more terminal commands?

I don't want to reinstall because I fear the problem will just happen again.

Also, per last reply I have posted my xorg.0.log file in two attachments. I read it over and didn't notice anything, but much like Hijackthis files, you have to have the eyes i guess.
Many thanks for the help.

---

### Post by BicyclerBoy on 2012-06-20
Don't see anything in the log..
You using display LVDS so I guess this is a laptop internal screen..

I seem to remember recent bugs in the internal screen detection/activation.

Not a solution but ..
Can you use an external monitor?

---

