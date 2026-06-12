---
title: "Ghosting on Live TV Kodi frontend"
date: 2014-12-17
forum: Mythbuntu
---

### Post by hollywoodpete on 2014-12-17
I have been using Kodi on Ubuntu 14.04 as my frontend into an LG 1080 LED TV with an AMD Duel core APU with a 610 series video card. Movies and recorded TV Shows are fine when I use a NAS device. My backend is 64-bit Mythbuntu on on an Intel Poweredge 860 blade server with a duel core 3.0ghz processor with 4GB RAM and HDHomeRune Prime and Duel as  the source. I get an annoying ghosting at times watching live channels in spite of a gigabit hardwired network. I am convinced it is due to transcoding problem on my backend. I would think my hardware is sufficient (maybe overkill). I can live with it but would be much happier if the picture was perfect. The ghosting happens during fast action scenes or when embedded subtitles are on the bottom of the screen. If there is an easy fix, let me know

---

### Post by Lester_Burnham on 2014-12-18
Hi,

Have you tried watching a recording with VLC to see if it's the recording or the frontend.

Lester

---

### Post by hollywoodpete on 2014-12-18
> **Lester_Burnham said:**
> Hi,

Have you tried watching a recording with VLC to see if it's the recording or the frontend.

Lester

Watching the recorded episodes with Kodi and VLC is fine. It is only the Live TV that causes the issue and it is at variable times and channels making it hard to reproduce.

---

### Post by Lester_Burnham on 2014-12-18
Hi,
What about watching Live TV in mythfrontend on the same machine that has Kodi & VLC.
Best to test it with mythfrontend to get the support.

Does the backend log show up anything while watching Live TV? Have it open in SSH.
```
tail -f /var/log/mythtv/mythbackend.log
```
Lester

ps: what is this "AMD Duel core APU with a 610 series video card" an AMD Dual core APU? with Nvidia 610 graphics?

---

### Post by hollywoodpete on 2014-12-19
> **Lester_Burnham said:**
> Hi,
What about watching Live TV in mythfrontend on the same machine that has Kodi & VLC.
Best to test it with mythfrontend to get the support.

Does the backend log show up anything while watching Live TV? Have it open in SSH.
```
tail -f /var/log/mythtv/mythbackend.log
```
Lester

ps: what is this "AMD Duel core APU with a 610 series video card" an AMD Dual core APU? with Nvidia 610 graphics?

You are correct about the hardware.

tail -f /var/log/mythtv/mythtvbackend.log

[http://pastebin.com/n0QGP3Lu](http://pastebin.com/n0QGP3Lu)
With the LiveTV off

[http://pastebin.com/s2TMN3vi](http://pastebin.com/s2TMN3vi)
With live TV on

I did this with Kodi(XBMC) frontent. For some reason I can only see over the air channels on the Myth frontend. I will need to figure the Myth frontend out a little better

---

### Post by Lester_Burnham on 2014-12-19
> **hollywoodpete said:**
> [http://pastebin.com/n0QGP3Lu](http://pastebin.com/n0QGP3Lu)
With the LiveTV off

There's a couple of errors in this log. Maybe not helping mythfrontend working correctly.
```
Dec 19 12:00:48 homer mythbackend: mythbackend[29361]: **E** CoreContext storagegroup.cpp:763 (CheckAllStorageGroupDirs) SG(ChannelIcons): Group 'ChannelIcons' wants to use directory '/home/nighthawk/.mythtv/channels/', but this directory is not writeable.
Dec 19 12:00:45 homer mythbackend: mythbackend[29361]: **E** CoreContext mythtranslation.cpp:73 (load) Error Loading en_us translation for module mythfrontend
Dec 19 12:00:46 homer mythbackend: mythbackend[29361]: **W** CoreContext scheduler.cpp:213 (VerifyCards) Scheduler: Listings source '' is defined, but is not attached to a card input.
```


There's errors in here too, but they don't mean anything to me wothout searching google.
> [http://pastebin.com/s2TMN3vi](http://pastebin.com/s2TMN3vi)
With live TV on
```
nighthawk@homer:~$ tail -f /var/log/mythtv/mythbackend.log
Dec 19 12:25:23 homer mythbackend: mythbackend[29361]: I TVRecEvent tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[5]: HW Tuner: 5->5
Dec 19 12:25:23 homer mythbackend: mythbackend[29361]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Dec 19 12:25:23 homer mythbackend: mythbackend[29361]: **E** HDHRStreamHandler recorders/dtvsignalmonitor.cpp:322 (HandlePAT) DTVSigMon[5](131E235D-0): Program #0 not found in PAT!#012Program Association Section#012 PSIP tableID(0x0) length(13) extension(0x0)#012      version(0) current(1) section(0) last_section(0)#012      tsid(0) programCount(1)#012  program number     3 has PID 0x003d
Dec 19 12:25:23 homer mythbackend: mythbackend[29361]: **E** HDHRStreamHandler recorders/dtvsignalmonitor.cpp:328 (HandlePAT) DTVSigMon[5](131E235D-0): But there is only one program in the PAT, so we'll just use it
Dec 19 12:25:23 homer mythbackend: mythbackend[29361]: N HDHRStreamHandler recorders/dtvsignalmonitor.cpp:367 (HandlePMT) DTVSigMon[5](131E235D-0): PMT says program 3 is encrypted
Dec 19 12:25:24 homer mythbackend: mythbackend[29361]: **E** HDHRStreamHandler recorders/hdhrstreamhandler.cpp:206 (UpdateFilters) HDHRSH(131E235D-0): UpdateFilters called in wrong tune mode
Dec 19 12:25:24 homer mythbackend: mythbackend[29361]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Dec 19 12:25:24 homer mythbackend: mythbackend[29361]: **E** TVRecEvent recorders/recorderbase.cpp:206 (SetStrOption) RecBase[5](131E235D-0): SetStrOption(...recordingtype): Option not in profile.
Dec 19 12:25:25 homer mythbackend: mythbackend[29361]: I ProcessRequest mainserver.cpp:1538 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Dec 19 12:25:25 homer mythbackend: mythbackend[29361]: I ProcessRequest mainserver.cpp:1540 (HandleAnnounce) adding: xbmc as a remote file transfer
```

> I did this with Kodi(XBMC) frontent. For some reason I can only see over the air channels on the Myth frontend. I will need to figure the Myth frontend out a little better
That's all I get here in OZ, so not sure what you mean by that. Maybe the error to do with channels directory permissions, may help that, even though I'm pretty sure that's only where the icons are stored.

Lester

---

