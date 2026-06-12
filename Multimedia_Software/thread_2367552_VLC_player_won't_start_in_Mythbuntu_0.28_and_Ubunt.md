---
title: "VLC player won't start in Mythbuntu 0.28 and Ubuntu 14.04LTS"
date: 2017-07-31
forum: Multimedia Software
---

### Post by MBEeng on 2017-07-31
After upgrading Mythbuntu to 0.28 running on Ubuntu 14.04LTS, I can not use VLC player to play DVDs in  MythTV optical disks, though the default player still works. 

If I change the setup under 
Setup>Media Settings>Videos Settings>Player Settings to


**Default player:** vlc
 **DVD player:  **vlc %d
 **DVD drive**:  default     (or **DVD drive**:  /dev/sr0 )

then attempt to play a DVD from the Optical Disk menu, nothing happens.  The VLC player doesn't open, the MythTV menu continues to display.

This has become an issue because several DVDs recently hang up before starting, apparently just before the FBI warning, in the default MythTV DVD player, but will run under VLC on my desktop computer.  (for example, Silicon Valley season 3 and Republic of Doyle season 5).

I can't use VLC without MythTV in the underlying Ubuntu system end because HDMI audio has disappeared from Ubuntu, but still works in MythTV.  I'm afraid that attempts to fix the Ubuntu HDMI sound will mess it up in MythTV.  The video driver is the proprietary AMD Catalyst driver.

---

