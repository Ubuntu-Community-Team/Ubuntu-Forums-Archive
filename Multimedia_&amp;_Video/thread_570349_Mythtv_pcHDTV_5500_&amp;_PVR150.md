---
title: "Mythtv pcHDTV 5500 &amp; PVR150"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by RoyalPro on 2007-10-08
I have Ubuntu Gutsy install with Mythtv.  I have had the PVR150 running for some time now and have just added a pcHDTV 5500.  I can get the analog channels to show up with V4l and the analog under the DVB drivers.  I can't get any of the digital drivers to show up and if I use the tools dtvscan it says it can't find the device /dev/dtv.  The kernel has built in support for the card, but I still tried installing the drivers for the card with no luck.  Also when I change to the analog channels on the 5500 the video is choppy and the sound is squeaky.  If you need any more info let me know.

---

### Post by freddyg on 2007-10-11
dont know if im reading your post right, but install dvb-utils and then do a "sudo modprobe cx88-dvb"
jump into mythtv-setup and add a new dvb card...still working on this, hope it helps, if not, sorry
got some info from [https://wiki.ubuntu.com/MythTVTeam/MythTVHardwareSupport?highlight=%28CategoryMythTV%29](https://wiki.ubuntu.com/MythTVTeam/MythTVHardwareSupport?highlight=%28CategoryMythTV%29)

---

### Post by freddyg on 2007-10-13
this is more along the lines of what i was thinking before, see: [https://help.ubuntu.com/community/MythTV_Feisty_hardware_list?highlight=%28pchdtv%29](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list?highlight=%28pchdtv%29)

---

