---
title: "screen resolution - 1280x1024 missing"
date: 2010-05-28
forum: Multimedia Software
---

### Post by DouglasAdams on 2010-05-28
//CLOSED//                       excellent, easy to understand solution

screen resolution - 1280x1024 missing


my xorg.conf contains:

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

yet my System > Preferences > Monitor
shows five different resolutions & Monitor: Unknown.
from what i think i understand from reading:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
this seems wrong.
i would have expected to see the 5 screen resolutions in the xorg.cong file

i'm very wary about making any changes since i've just managed to totally screw my fstab file. (as i still had lots of silly problems after "upgrading" to 10.04, i decided to do a re-install from the live cd)

previously, on 9.10 and my upgraded 10.04, i had been using 1280x1024 (or 960)
after installing using the live cd all i've got is
1360x768, 1024x768 and smaller

please, please, please
how do i get one of the 1280 resolutions back?

---

### Post by jerrrys on 2010-05-29
at the risk of repeating the wiki

[http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)

pretty painless i thought

---

### Post by drreed on 2010-05-30
> **jerrrys said:**
> at the risk of repeating the wiki

[http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)

pretty painless i thought


As near as I can tell, there isn't one valid command on that entire page, but I'm using Xubuntu 9.10 on this laptop . . .

---

### Post by lykwydchykyn on 2010-05-30
xorg is mostly automated these days, so the xorg.conf is usually pretty sparse.  The only reason to put something in it is to override what xorg autodetects about your hardware.  

Which is what we need to do in this case.

So, after the line "DefaultDepth 24" and before the line "EndSection" (in the "Screen" section), add these lines:
```

SubSection "Display"
Depth 24
Modes "1280 x1024" "1280 x 960"
EndSubSection

```

Then restart Xorg (or just reboot) and see what that gets you.

---

### Post by DouglasAdams on 2010-05-31
many, many thanks lykwydchykyn.
i did as you said and i've now got just about every screen size ever made (god knows how or why).
fact is, i lost my confidence in ubuntu with all the nagging problems i had when i upgraded from 9.10 to 10.04
then i lost confidence in myself when i managed to screw-up my fstab and ended up re-installing.
your advice was exactly what i needed, a step by step explanation of what to do and why.

i certainly didn't need the curt reply from jerrrys
- especially after seeing the alarm bells set ringing after reading the post by drreed.

thanks drreed and thanks again lykwydchykyn,
you are the spirit of Linux in general and Ubuntu in particular.

---

### Post by MoragSorcha on 2010-06-02
I have had the same problem as DouglasAdams, except I need a screen resolution of 1024 x 768. The instructions in this thread look easy to follow but as a newbie I would like help locating the xorg.conf file. I gather from looking at other help fora that it should be in /etc/X11 but it isn't! I'm using Xubuntu 10.4 by the way. Please could someone tell me where to find it and the command for editing it. Many thanks!

---

### Post by DouglasAdams on 2010-06-03
> **MoragSorcha said:**
> I have had the same problem as DouglasAdams, except I need a screen resolution of 1024 x 768. The instructions in this thread look easy to follow but as a newbie I would like help locating the xorg.conf file. I gather from looking at other help fora that it should be in /etc/X11 but it isn't! I'm using Xubuntu 10.4 by the way. Please could someone tell me where to find it and the command for editing it. Many thanks!

standing on the shoulders of giants, i give you:

Open a terminal, and type in
```

sudo gedit /etc/X11/xorg.conf

```
quote:  dbott67 circa 2005

sorry i didn't include this earlier.
wanna let us know how you went on morag?

---

### Post by c0rrupt0r on 2010-06-03
I have done these steps and with my nvidia card and settings it did not change a thing and did not add those resolutions any more ideas?

---

### Post by DouglasAdams on 2010-06-03
> **c0rrupt0r said:**
> I have done these steps and with my nvidia card and settings it did not change a thing and did not add those resolutions any more ideas?
you edtied the file as per post # 7,
then you added the lines to your conf file as per post # 4,
then exited and saved it?
and rebooted to grab the new file?

if you have done all these things then that's as far as my "knowledge" goes, sorry.

---

### Post by MoragSorcha on 2010-06-04
> **lykwydchykyn said:**
> xorg is mostly automated these days, so the xorg.conf is usually pretty sparse.  The only reason to put something in it is to override what xorg autodetects about your hardware.  

Which is what we need to do in this case.

So, after the line "DefaultDepth 24" and before the line "EndSection" (in the "Screen" section), add these lines:
```

SubSection "Display"
Depth 24
Modes "1280 x1024" "1280 x 960"
EndSubSection

```Then restart Xorg (or just reboot) and see what that gets you.

I have found xorg but it's called xorg.conf.d and it contains the following: 05-evdev.conf  10-synaptics.conf  10-vmmouse.conf  10-wacom.conf - none of these contain the line "Default Depth". Where should I look to put the above SubSection?  I'm determined to get there in the end!  Appreciate any help!

---

### Post by lykwydchykyn on 2010-06-04
/etc/X11/xorg.conf does not exist by default.  You will have to create it, and if it doesn't exist already you can't just put in the bit I added.

Probably the most reliable way to create it is to follow the instructions on this page: [https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

---

