---
title: "Frontends crashing on previously stable system"
date: 2008-08-17
forum: Mythbuntu
---

### Post by allene222 on 2008-08-17
I have an Mythbuntu 8.04, AMD 5400+, Nvidia 6200, 2 air2pc, 1HDHR, spdif audio system.  It worked fine for 2 months but lately it gets into a mode where you can't watch anything.  It either freezes, or the video is a gray screen with a little digital noise.  My mythfrontend log shows errors, the backend log looks fine.  MySQL log looks fine and the status of MySQL shows all OK.  Did a DB scan/fix and it did not fix the problem.  e2fsck was fine.

A typical test session goes like this (I will use one episode of GMA as a test show).
1) Watch GMA and exit back to main menu -- fine
2) Do this again twice more -- fine
3) On the 4th time, the show is just the gray screen
4) On the 5th time, X locks up.
5) Reboot, restart-X, bunch of stuff to get the system back
6) Watch GMA (entire hour) and it is fine.
When the show plays, the frontend log is clean, when it didn't play, I got messages like this:
2008-08-16 15:01:13.507 [mpeg2video @ 0xb7400b88]ac-tex damaged at 21 0

There is nothing special about GMA, I get the same behavior on any show.  We watched the olympics last night for 4 hours and everything looked fine but the frontend log was showing audio errors several a second.
2008-08-17 00:03:05.550 NVP::AddAudioData() : p1 : Audio buffer overflow,


This morning, watching a show everything looked fine but TOP has Xorg showing 98% CPU.

The funny thing is that everything points to the frontend but I have two frontends and when the machine gets into this state, both frontends act the same, even if one was off when the problem happened and turned on to check if it will work.

The system worked fine for at least a week since the last thing I did, which was to just enable NFS and change the re-boot timer to 3 seconds.  Now, it will crash several times a day.

I really need help!!!!

Allen

---

### Post by allene222 on 2008-08-19
It looks like this is an issue where MythTV will not play things recorded on KQED 9.1 in San Francisco ATSC (OTA).  I am talking with the engineering folks there and doing some experiments.  It does not look like it is something wrong with my system. They have some header issue and Myth apparently freaks out because of it.

These shows will play in mplayer if I didn't say that before.  They totally lock up mythfrontend if you even let the show grap a preview.  If you are really fast with the remote and avoid any KQED show, you can watch anything else.  We have seen this on 4 reported systems so far.

Allen

---

### Post by allene222 on 2008-08-23
Nobody replied to this but here is what is going on:
KQED in San Francisco has a header problem and the HDHR passes the sub channel to MythTv in such a way that it caused mythfrontend to basically crash.  Any other station is fine, record with another capture device and it is fine, play the file with mplayer and it is fine.  It takes all three, KQED, HDHR, MythTV to cause a crash.

I have filed a bug report with Myth, and Silicon Dust. I have reported it to the VP Engineering at KQED.

Work around it to use another capture card for KQED.

Allen

---

