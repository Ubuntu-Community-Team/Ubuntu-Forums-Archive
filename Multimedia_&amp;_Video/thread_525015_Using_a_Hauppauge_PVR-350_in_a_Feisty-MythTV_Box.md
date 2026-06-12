---
title: "Using a Hauppauge PVR-350 in a Feisty-MythTV Box"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by RonnieV on 2007-08-13
I'm a struggling newbie putting my first MythTV box together using Feisty as my underlying linux distro. I have a Hauppauge PVR-350 card installed and am able to watch and record TV.  However, for the last several evenings I have tried unsuccessfully to get MythTV to allow me to use the PVR-350's TV Out/MPEG decoder.

I'm using the info found within "https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out" in order to accomplish the step of my installation.

I've successfully edited /etc/modprobe.d/aliases to include the line "options ivtv-fb osd_compat=1". However, when I enter the Frontend's Utilities-Setup/Setup/TV Settings/Playback and check the box requesting MythTV to "Use the PVR-350's TV/Out/MPEG decoder" I am unable to restart MythTV.  I get an error message stating that MythTV is "Uanable to initialize video." Moreover, when I attempt to load the ivtv driver using the command "modprobe ivtv-fb", I'm told that the "operation not permitted".

If anyone has experience using Hauppauge's PVR-350 perhaps you can tell me where I've gotten off course, or direct me to another recipe designed to take full advantage of the card's ability to handle the decoding.  TIA for your input.

---

