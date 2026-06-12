---
title: "LIRC setup, now how do I enable IR remote in VLC?"
date: 2009-04-26
forum: Multimedia Software
---

### Post by gdbutcher on 2009-04-26
I used the excellent mythbuntu-lirc-generator to create the LIRC for my MCE Vista remote. MythTV and Mplayer both found the remote without any further setting up, but its not working with VLC.

It should, do I have to enable it in VLC or something? if so, how?

**or**

Can you suggest a way of configuring Mplayer to display videos with the correct aspect ratio? My resolution is 1920x1080. in full screen mode Mplayer squahes the image horizontaly by 1 & 1/2 inches both sides even when i choose the 16:9 option. Whereas VLC displays full screen with the correct resolution:confused:

---

### Post by Spectre5 on 2009-11-13
> **gdbutcher said:**
> I used the excellent mythbuntu-lirc-generator to create the LIRC for my MCE Vista remote. MythTV and Mplayer both found the remote without any further setting up, but its not working with VLC.

It should, do I have to enable it in VLC or something? if so, how?

**or**

Can you suggest a way of configuring Mplayer to display videos with the correct aspect ratio? My resolution is 1920x1080. in full screen mode Mplayer squahes the image horizontaly by 1 & 1/2 inches both sides even when i choose the 16:9 option. Whereas VLC displays full screen with the correct resolution:confused:

It doesn't want to work with VLC for me either...did you get this working?

---

### Post by Spectre5 on 2009-11-13
> **Spectre5 said:**
> It doesn't want to work with VLC for me either...did you get this working?

AH:

Tools->Preferences
Show settings->All (bottom left, select all)
Expand Interface
Select Control Interfaces
Check "Infrared remote control interface"
Save, close, restart VLC
Enjoy!

---

### Post by tidris on 2009-11-14
For the aspect ratio issue, have you tried the "-noaspect" mplayer option?

---

