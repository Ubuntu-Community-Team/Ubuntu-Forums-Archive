---
title: "amd driver not working after upgrade"
date: 2013-05-03
forum: Multimedia Software
---

### Post by BcRich on 2013-05-03
Hi,
After upgrading to 13.04 my display no longer works as expected.
I have a primary display running off an amd HD6850 and a secondary display running off an amd HD4290
This configuration worked well in 12.04 and 12.10.
When i try to launch amdcccle in 13.04 i can only do so through terminal, as clicking a menu item does not work. 
Any changes I make within amdcccle disappear after reboot, as a result my system currently has no hardware acceleration.

I've tried manually installing the latest drivers from amd's website and tried changing which driver is in use in software sources, none of these options work.

Please help, I really need to get back to work and not fiddle with os upgrade issues anymore.
Thanks

---

### Post by BcRich on 2013-05-03
here's the output from amdcccle when i try to change settings
```
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    155 (Uknown extension)
  Minor opcode: 66 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    154 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    154 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    154 (Uknown extension)
  Minor opcode: 14 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    155 (Uknown extension)
  Minor opcode: 66 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    154 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    154 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    154 (Uknown extension)
  Minor opcode: 14 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    155 (Uknown extension)
  Minor opcode: 94 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    155 (Uknown extension)
  Minor opcode: 94 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    155 (Uknown extension)
  Minor opcode: 66 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    154 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    154 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    154 (Uknown extension)
  Minor opcode: 14 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    155 (Uknown extension)
  Minor opcode: 66 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    154 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    154 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    154 (Uknown extension)
  Minor opcode: 14 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    155 (Uknown extension)
  Minor opcode: 95 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    155 (Uknown extension)
  Minor opcode: 95 (Unknown request)
  Resource id:  0x17
[xcb] Unknown sequence number while appending request
[xcb] Most likely this is a multi-threaded client and XInitThreads has not been called
[xcb] Aborting, sorry about that.
amdcccle: ../../src/xcb_io.c:160: append_pending_request: Assertion `!xcb_xlib_unknown_seq_number' failed.


```

---

### Post by BcRich on 2013-05-03
the error I get when I try to start Blender
```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  155 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  49
  Current serial number in output stream:  49


```

---

### Post by QIII on 2013-05-03
*Moved to** Multimedia & Video.***

Hello!  Sorry to hear about the problem.

It is not at all surprising that your system is not working.  In fact, I would expect that.

What *is *surprising is that it worked with 12.10.

All HD4000 and prior cards have been moved to a legacy driver branch.  The driver will not work with X Server 1.13, which is used with both 12.10 and 13.04.  With a mixed pair like that, you won't get the proprietary driver to work.  You can only use the default open source Radeon driver.

If your newer card has the ports to do it, you would probably be better off ditching the HD4000 and using only the newer card.

This is not an issue with upgrading to a newer Ubuntu.  It is an issue with AMD/ATI choosing not to continue development on the driver for their older cards.

Wish I had better news.

Regards.

---

### Post by 2F4U on 2013-05-03
My understanding is that ATI dropped support for the HD 4X series, so they won't work with 13.04.

[http://ubuntuforums.org/showthread.php?t=2139644](http://ubuntuforums.org/showthread.php?t=2139644)

---

### Post by BcRich on 2013-05-03
Hi QIII
Thanks for the reply.
The outputs that I posted were from my system after I had disabled the HD4290 in BIOS, removed my previous radeon drivers and configuration files and reinstalled the catalyst 13.4 driver with only my HD6850 active.
I've also tried just using the default Xorg xserver open source drivers (without any of the proprietary drivers installed) but this didn't work either.
I figured this is related to upgrades as this is a configuration (i.e. without the HD4290 installed) that worked with previous Ubuntu versions but not with 13.04?

---

### Post by BcRich on 2013-05-04
Thanks for the help QIII and 2F4U :)
I basically managed to get my system back to a stable state by uninstalling the proprietary amd drivers and am currently using the xserver xorg open source drivers. As a large majority of the work I do involves using Blender I've been reluctant to use the open source drivers as I thought performance would be compromised in comparison to the amd proprietary drivers. However, having tested the open source drivers a couple of times now in 13.04 I can't say that I notice any visible difference in performance when working with Blender. As a result I'm going to stick with the open source drivers and follow QIII's suggestion of running the second monitor off of the HD6850.
If I notice any visible difference with the open driver compared to the proprietary one I'll post back here.
Thanks again for your help, it's very much appreciated :)

---

### Post by BcRich on 2013-05-04
After using the opensource drivers for a while i came across a major bug, in blender the system will appear to hang when trying to make a click selection.i tested this in blender 2.66a, 2.65 and 2.64, plus tested with kubuntu 13.04 and xfce 13.04 all with the opensource org xserver driver. making a selection of a simple object such as a cube with a minimal polycount does not cause the system to hang. but selecting a complex 3D object does cause blender to hang, and by complex i mean something more complex than a multi-subdivided cude. 
i discovered that the problem i was having with my previous config was that uname -r was revealing that i was using an old kernel as the new one was not appearing in my grub menu, this is probably related to a botched system upgrade from a few days ago where grub failed to install correctly.
subsequently i used boot-repair to purge grub then reinstall it.
this restored by grub menu to an acceptable state, with fewer options and loaded the newer 3.8.0.19-generic kernel appropriatly. i then reinstallled the propriatry drivers which worked this time, except for a logo that appeared at the bottom of the screen reading "Unsupported Hardware" I was able to remove the logo using this wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide
So I can confirm that I have 13.04 running an AMD HD6850 with propriatry drivers loaded and Blender working as expected.

---

