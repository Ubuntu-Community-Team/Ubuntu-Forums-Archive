---
title: "3D Testing on Optimus NVidia (Ironhide) Dell L502x"
date: 2011-10-22
forum: Multimedia Software
---

### Post by cozumel on 2011-10-22
Hi,

I am a noob, just one week using Ubuntu as my primary OS.

I have just installed Ironhide to enable Optimus switching on NVidia card.


Everything so far good.  Just watched DVD 2 hours (Platoon) and played around on the system for another hour on battery power.

Now I want to test 3D.  Are there any specific programs that will drive NVidia card hard for testing please?  And what sort of fps should I be getting while testing please?

Full config:
Dell XPS L502x
4GB (2x2) 1333MHz DDR3 RAM
i7 2630QM
NVidia GeForce GT 540M
500GB WD Scorpio HDD
Intel Centrino 1030 wireless N / Bluetooth combo card
Battery: 6-cell 56W/HR LI-ION

Many thanks for your time and help

---

### Post by akoskm on 2011-10-28
You could try ironhide's test:
```

optirun

```
which provides me such output:
```

akoskm@turing:~$ optirun glxgears
 * Starting Ironhide X server ironhide                                          _PS0 Enabling nVidia Card failed (Error: AE_NOT_FOUND).
.                                                                        [ OK ]
5083 frames in 5.0 seconds = 1016.403 FPS
3813 frames in 5.0 seconds = 762.451 FPS
5424 frames in 5.0 seconds = 1084.643 FPS
5537 frames in 5.0 seconds = 1107.286 FPS
 * Stopping Ironhide X server ironhide                                          NVOP Disabling nVidia Card failed (Error: AE_NOT_FOUND).
_PS3 Disabling nVidia Card failed (Error: AE_NOT_FOUND).

```.

I found interesting that it failed with both disabling/enabling the nvidia card. Wondering does it work at all...

---

### Post by lafoman on 2011-11-21
> **cozumel said:**
> Hi,

I am a noob, just one week using Ubuntu as my primary OS.

I have just installed Ironhide to enable Optimus switching on NVidia card.


Everything so far good.  Just watched DVD 2 hours (Platoon) and played around on the system for another hour on battery power.

Now I want to test 3D.  Are there any specific programs that will drive NVidia card hard for testing please?  And what sort of fps should I be getting while testing please?

Full config:
Dell XPS L502x
4GB (2x2) 1333MHz DDR3 RAM
i7 2630QM
NVidia GeForce GT 540M
500GB WD Scorpio HDD
Intel Centrino 1030 wireless N / Bluetooth combo card
Battery: 6-cell 56W/HR LI-ION

Many thanks for your time and help

Hi there.
I have almost the same configuration that you, but I cannot make ironhide work. Do you remember which configuration did you select from the menu?
Thanks a lot!

---

