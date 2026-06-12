---
title: "Audio players only plays one song b4 ForceQuits"
date: 2008-04-07
forum: Multimedia &amp; Video
---

### Post by arki on 2008-04-07
My problem:   

Audio Players only plays one song before it force quits.

Ive been using Banshee for the past few months, the problem began when i was uninstalling Avidemux, DeVeDe, QDVDauthor. all removed from the comandline with apt-get and removed what was left with autoremove. I tryed installing other audio players beep, audacious and amarok; all had to be force-quit after one song. 

I ran Banshee from the CL and got this:
Debug: [07/04/2008 2:13:48 PM] (Loading audio profiles) - /usr/share/banshee/audio-profiles

Debug: [07/04/2008 2:13:48 PM] (Default player engine) - GStreamer 0.10

Debug: [07/04/2008 2:13:48 PM] (Audio CD Core Initialized) - 

Debug: [07/04/2008 2:13:48 PM] (Testing device for DAP support) - /org/freedesktop/Hal/devices/volume_uuid_1002BA8002BA69FC

Debug: [07/04/2008 2:13:48 PM] (Waiting for possible DAP to mount) - /org/freedesktop/Hal/devices/volume_uuid_1002BA8002BA69FC

Debug: [07/04/2008 2:13:48 PM] (DAP has not been added) - /org/freedesktop/Hal/devices/volume_uuid_1002BA8002BA69FC

Debug: [07/04/2008 2:13:48 PM] (Testing device for DAP support) - /org/freedesktop/Hal/devices/volume_uuid_8E96B68296B66A7B

Debug: [07/04/2008 2:13:48 PM] (Waiting for possible DAP to mount) - /org/freedesktop/Hal/devices/volume_uuid_8E96B68296B66A7B

Debug: [07/04/2008 2:13:48 PM] (DAP has not been added) - /org/freedesktop/Hal/devices/volume_uuid_8E96B68296B66A7B

Warning: [07/04/2008 2:13:48 PM] (Power Management Call Failed) - Cannot find GNOME Power Manager: Name org.gnome.PowerManager has no owner

Debug: [07/04/2008 2:13:48 PM] (Enabled multimedia keys support) - Using org.gnome.SettingsDaemon

Killed


GNOME Power Manager is installed (using a desktop) , I dont know what DAP is.

Any help is much appreciated.

---

