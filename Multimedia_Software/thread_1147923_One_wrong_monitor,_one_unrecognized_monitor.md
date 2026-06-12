---
title: "One wrong monitor, one unrecognized monitor"
date: 2009-05-03
forum: Multimedia Software
---

### Post by I Use Dial on 2009-05-03
I just did a fresh install of Jaunty on a new machine.  My trusty Gateway EV500 is showing up as a Gateway 2000 14" and my plasma TV doesn't show up at all.

The Gateway issue is a nuisance because I can't get the correct resolution.

The plasma TV not showing up is no surprise, but I'm not sure how to custom set the resolution.  The TV has a VGA port and the manual specifies all of the resolution settings that it accepts.

How do I fix these things?

---

### Post by I Use Dial on 2009-05-03
The EV500 issue isn't nearly as important to me as the plasma TV issue.  This is a media PC for my living room and I just want to set the video settings to work with the TV.

---

### Post by cariboo on 2009-05-04
If you have remote desktop enabled can you access the computer and change the resolution to something the TV can use? I had the same problem after an upgrade running Intrepid, after a reboot the resolution was set to 800X600 which my TV couldn't use. I used remote desktop to change the resolution to 1360X768 which works quite well. I'm running my media pc on an itnel atom motherboard with a 945 video chipset.

---

### Post by I Use Dial on 2009-05-04
Yep - remote desktop and SSH work quite well.  But how do I change the resolution?  Since the monitor is not recognized by Ubuntu, there are no options for different resolutions.

---

### Post by I Use Dial on 2009-05-04
I suppose I should mention that I've tried the sudo dpkg-reconfigure -phigh xserver-xorg and I don't get any sort of wizard.  The only thing I get is a warning saying it is overwriting a possibly-customised file and lists a backup location.

---

### Post by I Use Dial on 2009-05-04
Fixed!  I didn't change a thing, rebooted for a different reaston, and magically the resolution for WXGA showed up in the screen resolution options.

Mine's an Atom board also, went with the Jetway so I could get PCIe and PCI on the same board.  All I have to do now is figure out how to get LIRC working and then connect that to XBMC...

---

