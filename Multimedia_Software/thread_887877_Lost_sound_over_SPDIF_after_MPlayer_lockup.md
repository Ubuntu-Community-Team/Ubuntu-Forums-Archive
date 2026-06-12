---
title: "Lost sound over SPDIF after MPlayer lockup"
date: 2008-08-12
forum: Multimedia Software
---

### Post by Themicles on 2008-08-12
As the title says, I lost sound over my SPDIF out after Mplayer locked up while I was trying to get proper AC3 passthrough working with at least one player.

Rebooting does not help. Choosing different sound sources in Sound Preferences has no effect except when choosing p16v where the test tone does play but the left to right balance strongly favors the left.

The moment Ubuntu begins to boot, my surround sound receiver auto-detects Dolby Digital and switches to that mode. This is not normal and was not the behavior of the Ubuntu install before the MPlayer crash.

Also having a video issue: Having problems with players other than MPlyer and aspect ratios. Totem with the Xine back-end totally botches the aspect ratio of everything. I suspect it has something to do with the fact that my 32" HDTV doesn't report it's information properly. I managed to fix my DPI issues, but Totem with Xine screws up the height of any aspect ratio. The visual result is that it appears to be halving the height.

VLC also doesn't quite get aspect ratios right, but isn't quite as drastic as Totem w/ Xine.

---

### Post by Themicles on 2008-08-12
An update:

I tried uninstalling and reinstalling sound drivers per the Comprehensive Sound Problem Solutions Guide stickied in this forum. It had absolutely no effect. I uninstalled and reinstalled the list in the guide (as well as gdm and ubuntu-desktop) then rebooted. The moment before the login screen came up, my surround sound receiver detected Dolby Digital and switched modes. In case anyone is wondering, it's not a hardware issue as I can boot into my Win2k install and all works fine.

---

### Post by Themicles on 2008-08-12
Solved:

I went into the Volume Control and enabled every last little option there was in the Preferences. I then made sure everything was unmuted, and started toggling switches on the Switches tab. IEC958 Optical Raw was enabled. When I disabled it, I got all my sound back.

My receiver still shows that it's in Dolby Digital mode, which was not the case on the fresh install of this system, nor with my Ubuntu Studio 7.10 install. In both of those cases, the receiver displayed that it was a PCM stream.

Of note: I set up a .asoundrc file and rebooted prior to finally taking the "press random buttons" approach. This may or may not explain my receiver continuing to display that it's in Dolby Digital mode.

---

### Post by generica on 2009-01-11
You can use the command 'iecset audio on' to fix this issue.  I had the same problem and figured it out today.



> **Themicles said:**
> Solved:

I went into the Volume Control and enabled every last little option there was in the Preferences. I then made sure everything was unmuted, and started toggling switches on the Switches tab. IEC958 Optical Raw was enabled. When I disabled it, I got all my sound back.

My receiver still shows that it's in Dolby Digital mode, which was not the case on the fresh install of this system, nor with my Ubuntu Studio 7.10 install. In both of those cases, the receiver displayed that it was a PCM stream.

Of note: I set up a .asoundrc file and rebooted prior to finally taking the "press random buttons" approach. This may or may not explain my receiver continuing to display that it's in Dolby Digital mode.

---

