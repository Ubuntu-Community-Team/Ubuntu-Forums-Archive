---
title: "X Windows crash!!!!  HELP!"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by dvlchd3 on 2007-07-15
The last time I shutdown my computer I had to hold the power button because kubuntu would not shut down the entire way.  I waited for 30 minutes and the computer was showing a blank screen, but was still on.

However, now that I have booted into it again, it seems X Windows has decided to not want to start up.  The login screen comes up fine, and it accepts my password, however, when it is about to load KDE, X Windows crashes and I get a blank screen.  tty1 says at the top:

> Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/[string of hex]) = sda3(8,3)
kinit: trying to resume from /dev/disk/by-uuid/[same string of hex]
kinit: No resume image, doing normal boot...

If i try to do 'startx' it says as far as I can see on screen:
> waiting for X server to shut down (**) RADEON(0): RADEONCloseScreen
(**) RADEON(0): RADEONDRIStop
(**) RADEON(0): RADEONDisplayPowerManagementSet(0,0x0)
(**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81f5b30)
(**) RADEON(0): RADEONRestoreMemMapRegisters() :
(**) RADEON(0):   MC_FB_LOCATION          : [mem location]
(**) RADEON(0):   MC_AGP_LOCATION        : [mem location]
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x00080002 0x00040001e 0x00000000 (0x0000bf00)
(**) RADEON(0): Wrote: rd=2, fd=30, pd=4
(**) RADEON(0): Disposing accel...
(**) RADEON(0): Disposing cusor info
(**) RADEON(0): Disposing DGA
(**) RADEON(0): Unmapping memory
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.


Is there a way to reinstall kde or X since that seems to be the problems, or can any of this information help someone to help me fix the problem without reinstalling X or KDE?

Thanks very much in advance...

DAN

---

### Post by pppZero on 2007-07-16
> **dvlchd3 said:**
> 
[Snip]
If i try to do 'startx' it says as far as I can see on screen:

waiting for X server to shut down (**) RADEON(0): RADEONCloseScreen
[/Snip]


I'm almost positive the actual culprit is just before that line :)

Run the following command to see the entire output of X,

```
$ less /var/log/Xorg.0.log
```

Lines to look for are ones starting with (EE) or (WW) (meaning Error, and Warning)
If you're completely lost, just post the whole thing ;)

Hopefully X will point its finger at what is going wrong :)

---

### Post by dvlchd3 on 2007-07-19
> (EE) RADEON(0): [agp] Could not bind
(EE) RADEON(0): [agp] AGP failed to initialize. Siabling the DRI.

(EE) AIGLX: Screen 0 is not DRI capable

(EE) xf860OpenSerial: Cannot ope device /dev/input/wacom
            No such file or directory.
Error opening /dev/input/wacom : success
[^^ above repeated 3 times in a row]

(WW) The directory "/usr/share/fonts/X11/crillic" does not exist.
               entry deleted from font path.

(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found

(WW) RADEON: Failed to detect secondary monitor, MergedFB/Clone mode disabled

(WW) RADEON(0): Direct rendering disabled

from my interpretation of the above, the warnings are mainly things linux does not support in my graphics card.  However, it looks like /dev/input/wacom is missing or corrupt.  If this is correct how do I go about restoring that, or fixing it?

Thanks

DAN

---

