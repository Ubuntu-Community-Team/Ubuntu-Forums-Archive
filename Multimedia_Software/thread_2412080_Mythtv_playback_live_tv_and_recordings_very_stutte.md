---
title: "Mythtv playback live tv and recordings very stuttery"
date: 2019-02-07
forum: Multimedia Software
---

### Post by Tadaen_Sylvermane on 2019-02-07
Recently did an upgrade to 18.04. Mythtv is practically unwatchable. I had it in a container on 18.04 on a 16.04 host and everything was fine. Now upgrading the host to 18.04, I've tried moving it to the host rather than a container. Big problems, wife is getting annoyed. The screen washes out occasionally. The audio is out of sync with the video. The video and audio practically stop altogether quite often.

```
top - 18:09:05 up 20 min,  3 users,  load average: 0.66, 1.01, 1.19Tasks: 232 total,   1 running, 156 sleeping,   0 stopped,   0 zombie
%Cpu(s):  8.5 us,  5.2 sy,  0.8 ni, 83.0 id,  1.8 wa,  0.0 hi,  0.7 si,  0.0 st
KiB Mem :  7587016 total,  1265228 free,  2700328 used,  3621460 buff/cache
KiB Swap:  1949692 total,  1949692 free,        0 used.  4310768 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 2883 kodimain  20   0 3562204 343184  99544 S  33.0  4.5   6:15.55 kodi-x11    
 1848 mythtv    20   0 5023580  85860  57036 S  12.2  1.1   2:44.45 mythbackend 
 2708 mcserver  20   0 5108148 880596  19980 S   4.0 11.6   3:20.47 java        
 4695 mcserver  20   0 5108148 869564  20012 S   4.0 11.5   3:06.96 java
```

Seeing nothing in the mythtv log during this time. It seems to think everything is fine. Defintely not fine though. This was working just fine before upgrading the host to 18.04. For storage I'm using mergerfs with snapraid. I seem to be having no read / write issues from my storage. Just playback problems.

*EDIT* Marking as solved for now. I found some activity about it trying to expire some recordings, but it couldn't because they didn't exist. Some googling led me to find that it gets itself stuck, kind of like in quicksand and the process overloads itself.

Solution - 

I did not have any recordings that were important to me, just some live tv. We DVR very few things. As such my googling led me to find that the DB was likely corrupted. I dumped my database, recreated, reconfigured, and restarted the service. Basically a fresh configuration. Everything is working wonderfully now. Just a corrupted database.

---

### Post by Tadaen_Sylvermane on 2019-02-07
Spoke to soon. Left it running while in the shower. Get out and its a stuttery mess, audio out of sync, all kinds of problems.

```
Feb  7 20:29:40 megalith mythbackend: mythbackend[1848]: E TVRecEvent recorders/recorderbase.cpp:232 (SetStrOption) RecBase[1](10434F80-0): SetStrOption(...recordingtype): Option not in profile.Feb  7 20:32:31 megalith mythbackend: mythbackend[1848]: N Expire autoexpire.cpp:251 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 14 min
Feb  7 20:34:31 megalith mythbackend: mythbackend[1848]: N Expire autoexpire.cpp:637 (SendDeleteMessages) Expiring 0 MB for 1042 at 2019-02-08T03:28:47Z => "The Office":"Sex Ed"
Feb  7 20:34:31 megalith mythbackend: mythbackend[1848]: N Expire autoexpire.cpp:637 (SendDeleteMessages) Expiring 0 MB for 1182 at 2019-02-08T03:29:27Z => "Tengo talento, mucho talento"
Feb  7 20:34:36 megalith mythbackend: mythbackend[1848]: N DeleteThread mainserver.cpp:2456 (DeleteRecordedFiles) DeleteRecordedFiles - recording id 5 filename /snapraid/pool/dvr/1042_20190208032847.ts
Feb  7 20:34:36 megalith mythbackend: mythbackend[1848]: N DeleteThread mainserver.cpp:2534 (DoDeleteInDB) DoDeleteINDB - recording id 5 (chanid 1042 at 2019-02-08T03:28:47Z)
Feb  7 20:34:37 megalith mythbackend: mythbackend[1848]: C HttpServer69 programinfo.cpp:340 (ProgramInfo) ProgramInfo(): Failed to find recorded entry for 5.
Feb  7 20:34:37 megalith mythbackend: mythbackend[1848]: C HttpServer80 programinfo.cpp:340 (ProgramInfo) ProgramInfo(): Failed to find recorded entry for 5.
Feb  7 20:34:42 megalith mythbackend: mythbackend[1848]: N DeleteThread mainserver.cpp:2456 (DeleteRecordedFiles) DeleteRecordedFiles - recording id 7 filename /snapraid/pool/dvr/1182_20190208032927.ts
Feb  7 20:34:42 megalith mythbackend: mythbackend[1848]: N DeleteThread mainserver.cpp:2534 (DoDeleteInDB) DoDeleteINDB - recording id 7 (chanid 1182 at 2019-02-08T03:29:27Z)
Feb  7 20:34:43 megalith mythbackend: mythbackend[1848]: C HttpServer80 programinfo.cpp:340 (ProgramInfo) ProgramInfo(): Failed to find recorded entry for 7.
Feb  7 20:34:43 megalith mythbackend: mythbackend[1848]: C HttpServer82 programinfo.cpp:340 (ProgramInfo) ProgramInfo(): Failed to find recorded entry for 7.
Feb  7 20:35:19 megalith mythbackend: mythbackend[1848]: W TFWWrite threadedfilewriter.cpp:571 (DiskLoop) TFW(/snapraid/pool/dvr/1421_20190208032941.ts:95): write(65424) cnt 20 total 1203200 -- took a long time, 1162 ms
Feb  7 20:36:31 megalith mythbackend: mythbackend[1848]: N Expire autoexpire.cpp:637 (SendDeleteMessages) Expiring 4 MB for 1182 at 2019-02-08T03:29:28Z => "Tengo talento, mucho talento"
Feb  7 20:36:31 megalith mythbackend: mythbackend[1848]: N Expire autoexpire.cpp:637 (SendDeleteMessages) Expiring 0 MB for 1421 at 2019-02-08T03:29:40Z => "Mi marido tiene más familia"
Feb  7 20:36:36 megalith mythbackend: mythbackend[1848]: N DeleteThread mainserver.cpp:2456 (DeleteRecordedFiles) DeleteRecordedFiles - recording id 8 filename /snapraid/pool/dvr/1182_20190208032928.ts
Feb  7 20:36:36 megalith mythbackend: mythbackend[1848]: N DeleteThread mainserver.cpp:2534 (DoDeleteInDB) DoDeleteINDB - recording id 8 (chanid 1182 at 2019-02-08T03:29:28Z)
Feb  7 20:36:37 megalith mythbackend: mythbackend[1848]: C HttpServer80 programinfo.cpp:340 (ProgramInfo) ProgramInfo(): Failed to find recorded entry for 8.
Feb  7 20:36:37 megalith mythbackend: mythbackend[1848]: C HttpServer82 programinfo.cpp:340 (ProgramInfo) ProgramInfo(): Failed to find recorded entry for 8.
Feb  7 20:36:42 megalith mythbackend: mythbackend[1848]: N DeleteThread mainserver.cpp:2456 (DeleteRecordedFiles) DeleteRecordedFiles - recording id 9 filename /snapraid/pool/dvr/1421_20190208032940.ts
Feb  7 20:36:42 megalith mythbackend: mythbackend[1848]: N DeleteThread mainserver.cpp:2534 (DoDeleteInDB) DoDeleteINDB - recording id 9 (chanid 1421 at 2019-02-08T03:29:40Z)
Feb  7 20:36:43 megalith mythbackend: mythbackend[1848]: C HttpServer80 programinfo.cpp:340 (ProgramInfo) ProgramInfo(): Failed to find recorded entry for 9.
Feb  7 20:36:43 megalith mythbackend: mythbackend[1848]: C HttpServer82 programinfo.cpp:340 (ProgramInfo) ProgramInfo(): Failed to find recorded entry for 9.
Feb  7 20:38:59 megalith mythbackend: mythbackend[1848]: W TFWWrite threadedfilewriter.cpp:571 (DiskLoop) TFW(/snapraid/pool/dvr/1421_20190208032941.ts:95): write(65424) cnt 20 total 1251704 -- took a long time, 1130 ms
Feb  7 20:39:16 megalith mythbackend: mythbackend[1848]: W TFWWrite threadedfilewriter.cpp:571 (DiskLoop) TFW(/snapraid/pool/dvr/1421_20190208032941.ts:95): write(65424) cnt 27 total 1673952 -- took a long time, 1524 ms
Feb  7 20:41:36 megalith mythbackend: mythbackend[1848]: W TFWWrite threadedfilewriter.cpp:571 (DiskLoop) TFW(/snapraid/pool/dvr/1421_20190208032941.ts:95): write(65424) cnt 22 total 1399660 -- took a long time, 1461 ms
Feb  7 20:44:06 megalith mythbackend: mythbackend[1848]: W TFWWrite threadedfilewriter.cpp:571 (DiskLoop) TFW(/snapraid/pool/dvr/1421_20190208032941.ts:95): write(65424) cnt 19 total 1188724 -- took a long time, 1448 ms
Feb  7 20:46:23 megalith mythbackend: mythbackend[1848]: W TFWWrite threadedfilewriter.cpp:571 (DiskLoop) TFW(/snapraid/pool/dvr/1421_20190208032941.ts:95): write(65424) cnt 19 total 1188348 -- took a long time, 1279 ms
Feb  7 20:47:31 megalith mythbackend: mythbackend[1848]: N Expire autoexpire.cpp:251 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 14 min
Feb  7 20:49:17 megalith mythbackend: mythbackend[1848]: W TFWWrite threadedfilewriter.cpp:571 (DiskLoop) TFW(/snapraid/pool/dvr/1421_20190208032941.ts:95): write(65424) cnt 17 total 1036632 -- took a long time, 1029 ms
Feb  7 20:50:36 megalith mythbackend: mythbackend[1848]: I TVRecEvent tv_rec.cpp:1088 (HandleStateChange) TVRec[1]: Changing from WatchingLiveTV to None
Feb  7 20:50:36 megalith mythbackend: mythbackend[1848]: N RecThread recorders/recorderbase.cpp:501 (FinishRecording) Finished Recording: Container: MPEG2-TS Video Codec: mpeg2video (1920x1080 A/R: 3 29.97fps) Audio Codec: ac3
Feb  7 20:50:36 megalith mythbackend: mythbackend[1848]: I TVRecEvent tv_rec.cpp:863 (FinishedRecording) TVRec[1]: FinishedRecording(1421_2019-02-08T03:29:41Z) damaged recq:<RecordingQuality overall_score="0" key="1421_2019-02-08T0$
Feb  7 20:50:36 megalith mythbackend: mythbackend[1848]: I MythSocketThread(83) mainserver.cpp:7643 (connectionClosed) Playback sock(55c4db2df480) 'megalith' disconnected
Feb  7 20:50:36 megalith mythbackend: mythbackend[1848]: I MythSocketThread(84) mainserver.cpp:7643 (connectionClosed) Monitor sock(55c4db2f58e0) 'megalith' disconnected
Feb  7 20:50:36 megalith mythbackend: mythbackend[1848]: I MythSocketThread(98) mainserver.cpp:7681 (connectionClosed) FileTransfer sock(55c4db2d4cc0) disconnected
```

Tail end of /var/log/mythtv/mythtvbackend.log. Guessing my problem is those writes that "took a long time".

---

### Post by Tadaen_Sylvermane on 2019-02-08
Update. My ltsp pxe client is running off of the mythtv backend on this server / htpc and it works just fine. No problems at all. So my issue is likely with Kodi somewhere, maybe a bad upgrade on a driver or something. I've since purged all xorg, pulseaudio, kodi packages, openbox, and lightdm. Reinstalled. Issue still persists. But the bedroom box is running just fine. Something didn't upgrade correctly and I can't find it.

---

### Post by Tadaen_Sylvermane on 2019-03-04
Ok, final post on issue.

I have zero idea how to isolate this. I have eliminated the version of Mythtv being the issue, having built and or tried .28, .29 either bare metal or containers on an 18.04 host. Problem persists with 4k resolutions. No issue on 1080p or lower. I Have tried .28, .29 of mythtv on 16.04, and have zero issue both in and out of containers. I have eliminated both Leia and Krypton Kodi as the potential problems. Everything works great on 16.04 regardless of Kodi version. 18.04, both versions are screwy with 4k Mythtv playback. I can find zero errors in any logs that remotely seem connected with Xorg or graphical output. I've posted logs to Kodi forums, no results. I've combed over my Mythtv logs and googled damn near everything even remotely suspect in my eyes, no problems.

Ubuntu seems to be the culprit here yet I have no idea how one can track a problem based on just a symptom. All I know is that everything is fine on 16.04, terrible on 18.04 when Mythtv is involved on a 4k display. And if I'm the only one with this issue then it is twice as puzzling.

At this point I have no upgrade path until 20.04 releases, assuming whatever the problem is is fixed then. But I have no way of helping or directing anyone to the issue as again... no evidence beyond my eyes and ears. If anyone else has this issue, finds a fix, or whatever post here with what you've found or fixes please. I've run out of things to try where 18.04 is concerned. I'm guessing I'm missing a package, or an Xorg problem. Something that Myth relies on but the other stuff doesn't. Regardless, I'm giving it up for now. I may try again in a few months, maybe next year. I'm supported on 16.04 till 2021 so I've got time. I'm hoping to switch to try Debian again when Buster releases, but that will be awhile. For the time being my box is stuck on 16.04 and going nowhere. I hope someone finds this, and posts a fix, or something. Thanks again for views.

---

