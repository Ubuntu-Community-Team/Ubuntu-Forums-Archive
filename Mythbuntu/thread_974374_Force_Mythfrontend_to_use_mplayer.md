---
title: "Force Mythfrontend to use mplayer?"
date: 2008-11-07
forum: Mythbuntu
---

### Post by ajut on 2008-11-07
Hello,

Is is possible to force Mythfrontend (Mythbuntu 8.10) to use mplayer for LiveTV and recordings?

Why?

I get mpeg4-AVC from DVB-T which mplayer ([http://smplayer.berlios.de/forums/viewtopic.php?id=741](http://smplayer.berlios.de/forums/viewtopic.php?id=741)) can handle better than Mythfrontend internally .

BR,
Ajut

---

### Post by newlinux on 2008-11-07
I've seen this question asked a few times and various forums and never seen anyone explain how to do it. Only thing I can think of is to export your programs to mythvideo or add your livetv and storage group directories to your mythvideo directories and watch it through mythvideo using mplayer. You lose all the internal player functions though...

---

### Post by ajut on 2008-11-07
> **newlinux said:**
> I've seen this question asked a few times and various forums and never seen anyone explain how to do it. Only thing I can think of is to export your programs to mythvideo or add your livetv and storage group directories to your mythvideo directories and watch it through mythvideo using mplayer. You lose all the internal player functions though...

To bad :( I'm not sure anymore, if I can use MythTV at all :( One problem what drives me crazy is mythcommflag. It takes long time for mythcommflag to analyze 10 min of SD H264 and I get mythbackend.log full of " [h264 @ <0xb739e764>]number of reference frames exceeds max (probably corrupt input), discarding one" messages :(. It's possible to disable commercials finding system at all somewhere from mythtv-setup, I think. But still have that problem, if accessing "http://127.0.0.1/mythweb/tv/recorded" and PNG-s for newly recorded shows begin generated. Sometimes PNG-s are corrupted or even empty :(

Any suggestion?

---

### Post by newlinux on 2008-11-07
You can set your individual recording schedules not have commercial flagging in the recording options screens or from mythweb. You can disable all backends from being able to do commflagging in the mythtv-setup.

I'm guessing myth is just having problems processing the files, that is probably creating your corrup png problem...

---

