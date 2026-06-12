---
title: "Mythbuntu 11.10 No HD video...only SD"
date: 2011-10-15
forum: Mythbuntu
---

### Post by kismitt on 2011-10-15
I did a clean Install of Mythbuntu 11.10, but keeping old database from 11.04.  Everything seem to be working except can't watch any HD contents, only SD.  But I'm able to play all HD recording from VLC but not in MythTV.

I believe 11.10 removed "/etc/X11/xorg.conf" which I had to make some changes in 11.04 to get my video card to play HD contents.  Now I'm puzzle and don't know to fix it.

video card: Intel GMA x4500HD

*****************************************************************
OLD setting from Mythbuntu 11:04 (Xorg.conf)
# -----------------------------------------------------
Section "Device"
      Identifier  	       "Intel GMA X4500HD"
      Driver            	"intel"
      VendorName  	"Intel"
      BoardName     "G45 [Intel GMA X4500HD]"
      Option            "AccelMethod" "EXA"
EndSection

Section "Screen"
Identifier	               "Default Screen"
Monitor                	 "Configured Monitor"
EndSection

Section "DRI"
       Mode            0666
EndSection

Section "Module
   Load "dbe" # Double-Buffering Extension
   Load "v4l" # Video for Linux
   Load "extmod"
   Load "type1"
   Load "freetype"
   Load "glx" # 3D layer
   Load "dri" # direct rendering
EndSection

---

### Post by nickrout on 2011-10-15
I think what you need is the frontend log at the point where it fails to play.

---

### Post by kismitt on 2011-10-15
Launch Mythfrontend and then select SETUP and change the Playback setting to "High Playback" mode for 1080p.  That was it.  It had nothing to do with the video card setting.

---

### Post by thatguruguy on 2011-10-15
Feel free to mark this thread as solved if your problem is sorted out.

---

