---
title: "HDMI and HD Video not working (MythTV Interface and SD-Video Work)"
date: 2011-12-03
forum: Mythbuntu
---

### Post by jpummill2 on 2011-12-03
Hi Everyone,

Needing some help with my MythTV/Ubuntu 11.10 configuration.  After installing MythBuntu I can see the MythTV menus, XWindows, and SD-Video just fine.  When I try to play HD-Video I can make out the video but it looks "like an old school scrambled cable channel" as another poster wrote earlier.

I know the video recorded just fine because I can use MythWeb and VLC to view the recordings on my desktop computer.

I am using Intel video and audio hardware (see lspci output below):
[SIZE=1]00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01[/SIZE])

On a side note, audio doesn't seem to be working either (even for SD-Video).

Any insight would be most appreciated.

Thank you...

---

### Post by BC59 on 2011-12-03
I think you have to install the drivers for your Graphics card:

[http://www.ubuntu.com/certification/catalog/component/pci:2A42:8086-VIDEO](http://www.ubuntu.com/certification/catalog/component/pci:2A42:8086-VIDEO)

---

### Post by peskygnat on 2011-12-05
I am having the same problem.  Backend is still on 11.04, front end upgraded to 11.10.  Can see SD content, menus, web, can even full screen flash video in chromium no problem.  But HD videos in mythtv that looked great in 11.04 on this hardware look scrabbled with pink lines.  This is with opensource nvidia drivers, or the proprietary ones.

---

### Post by nickrout on 2011-12-05
Check your playback profiles - if you have a vdpau capable card, use the proprietary drivers and a vdpau profile.

If your card is not vdpau capable then make sure your profile does NOT use libmpeg2. It is broken in 11.10, and due to be phased out of myth in 0.25, so change now is good :)

---

