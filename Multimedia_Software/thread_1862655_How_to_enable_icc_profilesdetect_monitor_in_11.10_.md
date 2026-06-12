---
title: "How to enable icc profiles/detect monitor in 11.10  with nvidia."
date: 2011-10-17
forum: Multimedia Software
---

### Post by gwing on 2011-10-17
I need to be able to calibrate my monitor but am unable to do this since upgrading to 11.10 as my monitor type is not detected and looking at the colour manager/colord documents suggests this may be because the proprietary Nvidia drivers are incompatable.

With 11.04 I was able to simply de-activate the proprietary drivers & then all was weetness and light (OK I had no 3D but this is less important to me).  However de-actvating the proprietary drivers and switching to Unity 2D desktop still doesn't work under 11.10 i.e. no monitor detected so no icc profiling available.

Can anyone advise how I can go back to using the nouveau drivers in 11.10, or any other solution to get the monitor type detected properly?

---

### Post by sansblog on 2011-10-17
Problem for me too, but a bit different:
I'm using 2 monitors, and have done 2 icc profiles with dispcalgui/Argyll; only one of them seems to be active at a time ... and not with the "color" setting  in the systelm parameter window (like gwing).
I'm using the nvidia driver.

My printer is listed in the color control panel.

---

### Post by gwing on 2011-10-17
**[FONT=Arial][SIZE=2]Quoting direct from the colord FAQ (below) your problem with multiple monitors seems clearly defined. I just have the additional problem which I hope is just that the monitor type isn't being picked up and hence the icc calibration won't regard it as a valid target.[/SIZE][/FONT]**
 
-----------------
**Does calibration work with the NVIDIA binary driver?**
 
The binary driver from NVIDIA only supports XRandR 1.2, which means that it does not support per-monitor gamma tables. This means we can only send gamma correction tables to the screen, which means multiple monitor would not be supported. 
As the driver has no source code, we can't fix this and have to wait for NVIDIA to release a fixed version of their driver. Nowadays the open source nouveau driver provides a much better experience for NVIDIA hardware, and gnome-color-manager of course works flawlessly with all of the open source drivers.

---

### Post by sansblog on 2011-10-18
Thank you for your comment, gwing.
Windows seven: same problem: you do not apply the ICC profile through the Nvidia control Panel, but inside windows itself.

So, I should see my two monitors in the color control panel from gnome 3 ; you should see your monitor too. I do not know if this is a bug or if it's not implemented yet .
I shall search the net; if any information, then I'll report here.
Sorry for my english errors, I'm not an english native person.

---

### Post by sansblog on 2011-10-18
It seems it's a bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-color-manager/+bug/853056](https://bugs.launchpad.net/ubuntu/+source/gnome-color-manager/+bug/853056)

You can read:
[I]Status changed to 'Confirmed' because the bug affects multiple users.
...
[/I]                 [I]I believe this will not be fixed any time soon, as it's not a fault in Ubuntu.
The new Gnome 3 settings don't provide this functionality as of now.[/I]
 [I]As a workaround, you can do the following:
1. install argyll color management suite
2. create a file containing the following:
#!/bin/bash
dispwin /path/to/[/I]*your/icc/**profile.*[I]icc
3. make the file executable
4. add the newly created skript to your start programs[/I]

---

### Post by sansblog on 2011-10-18
I had to modify the script because of an error:
*XRandR 1.2 is faulty - falling back to older extensions*

Here is my new script; it's working fine upon startup ... for my main Asus screen only

#!/bin/bash
export ARGYLL_IGNORE_XRANDR1_2=true 
dispwin /home/sansblog/Calibration/Asus/Asus.icc

I don not need anymore to launch dispcal gui after each reboot !!!

But I still have to find how to apply a second Icc profile to my second Belinea monitor.
If someone knows how to do it ...

---

### Post by sansblog on 2011-10-18
As written by gwing, there is no support for dual screen calibration:

my new script is 

[I]#!/bin/bash
export ARGYLL_IGNORE_XRANDR1_2=true 
dispwin -d 1 /home/sansblog/Calibration/Asus/Asus.icc
dispwin -d 2 /home/sansblog/Calibration/Belinea/Belinea.icc[/I]


The last line generates this error:

*Dispwin: Error - We don't have access to the VideoLUT*

Larmes de crocodile !

---

### Post by JasonFH on 2011-10-23
Any way to make this run right from the start of ubuntu? pre-user login - and keep the icm profile up and running?

---

### Post by sansblog on 2011-10-25
> **JasonFH said:**
> Any way to make this run right from the start of ubuntu? pre-user login - and keep the icm profile up and running?
yes, it's easy: open the startup applications window (applications au démarrage into french)
Clic Add, fill name and command 
sh /home/you/yourcalibrationfolder/thenameofyourscript

My calibration is always loaded this way upon login !

---

