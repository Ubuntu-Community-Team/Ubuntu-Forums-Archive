---
title: "[SOLVED] 3d Rage Pro Turbo Hardware Acceleration"
date: 2008-08-02
forum: Multimedia Software
---

### Post by LittleFoot on 2008-08-02
I've been trying to get this thing to work for a bit without success.  I had compiled the dri and mesa drivers with undefined restults.  After installation of those I was able to get my gnome session going with a blank white screen.  Looking into the xorg.conf file and it's filled with things like

Section "Device"
	Identifier	"Configured Video Device"
EndSection

which is useless at least to me.  Even if it wasn't frustratingly blank I'm not sure which module I need to toss in as a driver.  Research suggests that I should have been able to dpkg-reconfigure xserver-xorg and the server should pick the correct one.  Any idea's appreciated.  I've been searching for 12+ hours without any satisfactory results.  From what I've found in google my chances are slim.  

Right now I've got good color and resolution but no direct rendering, this unfortunately makes video playback rather bad.  Right now I don't have any other cards that might fit the agp slot on the board and finances are very slim so no go on buying a cheap new card.
  
lspci -vv output

01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c) (prog-if 00 [VGA controller])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-

---

### Post by LittleFoot on 2008-08-04
Well further information from the Xorg.0.log shows that I am to short on video ram for direct rendering.  Nothing to be done about it I suppose.

---

