---
title: "&quot;Play DVD&quot; gives segfault"
date: 2010-08-16
forum: Mythbuntu
---

### Post by davelindquist on 2010-08-16
I'm using mythbuntu 10.04, and when I try to play a dvd (via the Play DVD option in the Optical Disks menu), I get a segfault.

Specifically, mythfrontend -v all gives:

```
2010-08-16 17:59:48.737 TV: StartPlayer(0, WatchingDVD, main) -- end ok
2010-08-16 17:59:48.737 TV: Changing from None to WatchingDVD
2010-08-16 17:59:48.737 NVP(0): ClearAfterSeek(1)
2010-08-16 17:59:48.737 VideoOutputXv: ClearAfterSeek()
2010-08-16 17:59:48.738 VideoOutputXv: DiscardFrames(0)
2010-08-16 17:59:48.738 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2010-08-16 17:59:48.738 MSqlQuery::exec(DBManager0) SELECT COUNT(name) FROM playgroup WHERE name <> 'Default' ORDER BY name; <<<< Returns 1 row(s)
2010-08-16 17:59:48.738 MSqlQuery::next(DBManager0) Result: "COUNT(name) = 0"
2010-08-16 17:59:48.741 TV: HandleStateChange(0) -- end
2010-08-16 17:59:48.738 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2010-08-16 17:59:48.742 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2010-08-16 17:59:48.743 StorageGroup::GetRelativePathname(dvd://dev/sr0)
2010-08-16 17:59:48.743 VDP: GetFilteredDeint() : xv-blit -> 'bobdeint'
2010-08-16 17:59:48.744 MSqlQuery::exec(DBManager0) SELECT DISTINCT dirname FROM storagegroup; <<<< Returns 1 row(s)
2010-08-16 17:59:48.744 MSqlQuery::next(DBManager0) Result: "dirname = /storage/recordings/"
2010-08-16 17:59:48.744 FilterManager: Loading filter '/usr/lib/mythtv/filters/libadjust.so'
2010-08-16 17:59:48.744 FilterManager: filters[adjust] = 0xa0c7578
2010-08-16 17:59:48.745 FilterManager: Loading filter '/usr/lib/mythtv/filters/libbobdeint.so'
2010-08-16 17:59:48.745 FilterManager: filters[bobdeint] = 0x9f425e0
2010-08-16 17:59:48.745 FilterManager: Loading filter '/usr/lib/mythtv/filters/libcrop.so'
2010-08-16 17:59:48.745 FilterManager: filters[crop] = 0xa599570
2010-08-16 17:59:48.745 FilterManager: Loading filter '/usr/lib/mythtv/filters/libdenoise3d.so'
2010-08-16 17:59:48.745 FilterManager: filters[denoise3d] = 0xa599128
2010-08-16 17:59:48.745 FilterManager: Loading filter '/usr/lib/mythtv/filters/libfieldorder.so'
2010-08-16 17:59:48.745 FilterManager: filters[fieldorderdoubleprocessdeint] = 0xa206188
2010-08-16 17:59:48.745 FilterManager: Loading filter '/usr/lib/mythtv/filters/libforce.so'
2010-08-16 17:59:48.745 FilterManager: filters[forceyv12] = 0xa209910
2010-08-16 17:59:48.745 FilterManager: filters[forceyuv422p] = 0xa206428
2010-08-16 17:59:48.745 FilterManager: filters[forcergb24] = 0xa2065a8
2010-08-16 17:59:48.745 FilterManager: filters[forceargb32] = 0xa599260
2010-08-16 17:59:48.745 FilterManager: Loading filter '/usr/lib/mythtv/filters/libgreedyhdeint.so'
2010-08-16 17:59:48.746 FilterManager: filters[greedyhdeint] = 0xa5993e0
2010-08-16 17:59:48.746 FilterManager: filters[greedyhdoubleprocessdeint] = 0xa205b38
2010-08-16 17:59:48.746 FilterManager: Loading filter '/usr/lib/mythtv/filters/libinvert.so'
2010-08-16 17:59:48.746 FilterManager: filters[invert] = 0xa205cc8
2010-08-16 17:59:48.746 FilterManager: Loading filter '/usr/lib/mythtv/filters/libivtc.so'
2010-08-16 17:59:48.746 FilterManager: filters[ivtc] = 0xa36cf58
2010-08-16 17:59:48.746 MSqlQuery::exec(DBManager0) SELECT DISTINCT data FROM settings WHERE value = 'VideoStartupDir'; <<<< Returns 2 row(s)
2010-08-16 17:59:48.746 MSqlQuery::next(DBManager0) Result: "data = "
2010-08-16 17:59:48.746 MSqlQuery::next(DBManager0) Result: "data = /storage/videos"
2010-08-16 17:59:48.746 FilterManager: Loading filter '/usr/lib/mythtv/filters/libkerneldeint.so'
2010-08-16 17:59:48.747 FilterManager: filters[kerneldeint] = 0xa36d098
2010-08-16 17:59:48.747 FilterManager: filters[kerneldoubleprocessdeint] = 0x9b69b40
2010-08-16 17:59:48.747 FilterManager: Loading filter '/usr/lib/mythtv/filters/liblinearblend.so'
2010-08-16 17:59:48.747 FilterManager: filters[linearblend] = 0x9fa29e8
2010-08-16 17:59:48.747 FilterManager: Loading filter '/usr/lib/mythtv/filters/libonefield.so'
2010-08-16 17:59:48.747 FilterManager: filters[onefield] = 0x9fa2ab0
2010-08-16 17:59:48.747 FilterManager: Loading filter '/usr/lib/mythtv/filters/libquickdnr.so'
2010-08-16 17:59:48.747 MSqlQuery::exec(DBManager1) SELECT mark, type FROM filemarkup WHERE filename = 'dvd://dev/sr0' AND type = '4' ORDER BY mark; <<<< Returns 0 row(s)
2010-08-16 17:59:48.747 FilterManager: filters[quickdnr] = 0xa33e768
2010-08-16 17:59:48.748 FilterManager: Loading filter '/usr/lib/mythtv/filters/libyadif.so'
2010-08-16 17:59:48.748 FilterManager: filters[yadifdeint] = 0xa36d378
2010-08-16 17:59:48.748 FilterManager: filters[yadifdoubleprocessdeint] = 0xa5994f0
2010-08-16 17:59:48.748 StorageGroup::GetRelativePathname(dvd://dev/sr0)
2010-08-16 17:59:48.748 FilterManager: GetFilterInfo(convert) returning: 0x0
2010-08-16 17:59:48.748 FilterManager: GetFilterInfo(bobdeint) returning: 0x9f425e0
2010-08-16 17:59:48.749 Using deinterlace method bobdeint
2010-08-16 17:59:48.749 MSqlQuery::exec(DBManager1) SELECT DISTINCT dirname FROM storagegroup; <<<< Returns 1 row(s)
2010-08-16 17:59:48.749 MSqlQuery::next(DBManager1) Result: "dirname = /storage/recordings/"
2010-08-16 17:59:48.749 New DB connection, total: 3
2010-08-16 17:59:48.751 MSqlQuery::exec(DBManager1) SELECT DISTINCT data FROM settings WHERE value = 'VideoStartupDir'; <<<< Returns 2 row(s)
2010-08-16 17:59:48.751 MSqlQuery::next(DBManager1) Result: "data = "
2010-08-16 17:59:48.751 MSqlQuery::next(DBManager1) Result: "data = /storage/videos"
2010-08-16 17:59:48.752 MSqlQuery::exec(DBManager0) SELECT mark, type FROM filemarkup WHERE filename = 'dvd://dev/sr0' AND type = '5' ORDER BY mark; <<<< Returns 0 row(s)
2010-08-16 17:59:48.752 No codec context. Returning false
2010-08-16 17:59:48.752 DVD Playback Debugging inDVDMenu 0 storedPacketcount 0 dvdstill 0
2010-08-16 17:59:48.752 AFD: DVD Title Changed
2010-08-16 17:59:48.752 Dec: Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2010-08-16 17:59:48.752 DVD Frame Rate 29.97
2010-08-16 17:59:48.753 Position map filled from DB to: 179
2010-08-16 17:59:48.753 Dec: SyncPositionMap prerecorded, from DB: 1 entries
2010-08-16 17:59:48.753 Dec: SyncPositionMap, new totframes: 179, new length: 6, posMap size: 1
2010-08-16 17:59:48.753 AFD: DVD Cell Changed. Update framesPlayed: 0 
2010-08-16 17:59:48.753 DVD Playback Debugging: mpeg seq end 0  inDVDStill 0 decodeStillFrame 0
2010-08-16 17:59:48.753 AFD: DVD Stream/Codec Change video_width 640 current_width 0 dvd_video_codec_changed 0
2010-08-16 17:59:48.753 DVD Playback Debugging: mpeg seq end 0  inDVDStill 0 decodeStillFrame 0
2010-08-16 17:59:48.753 AFD: DVD Stream/Codec Change video_width 640 current_width 0 dvd_video_codec_changed 0
Segmentation fault
```

...and cat /var/log/messages gives:


```
Aug 16 17:53:57 mythfront1 kernel: [100591.303695] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 16 17:53:57 mythfront1 kernel: [100591.303703] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Aug 16 17:53:57 mythfront1 kernel: [100591.303709] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Aug 16 17:53:57 mythfront1 kernel: [100591.303721] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 29 0f 00 00 00 40 00
Aug 16 17:53:59 mythfront1 kernel: [100593.423711] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 16 17:53:59 mythfront1 kernel: [100593.423719] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Aug 16 17:53:59 mythfront1 kernel: [100593.423724] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Aug 16 17:53:59 mythfront1 kernel: [100593.423736] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 29 11 c0 00 00 10 00
Aug 16 17:53:59 mythfront1 kernel: [100593.500068] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 16 17:53:59 mythfront1 kernel: [100593.500072] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Aug 16 17:53:59 mythfront1 kernel: [100593.500077] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Aug 16 17:53:59 mythfront1 kernel: [100593.500083] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 29 15 92 00 00 08 00
Aug 16 17:53:59 mythfront1 kernel: [100593.502684] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 16 17:53:59 mythfront1 kernel: [100593.502689] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Aug 16 17:53:59 mythfront1 kernel: [100593.502693] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Aug 16 17:53:59 mythfront1 kernel: [100593.502699] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 29 15 92 00 00 02 00
Aug 16 17:53:59 mythfront1 kernel: [100593.505312] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 16 17:53:59 mythfront1 kernel: [100593.505317] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Aug 16 17:53:59 mythfront1 kernel: [100593.505321] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Aug 16 17:53:59 mythfront1 kernel: [100593.505327] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 29 15 92 00 00 02 00
Aug 16 17:53:59 mythfront1 kernel: [100593.507981] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 16 17:53:59 mythfront1 kernel: [100593.507986] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Aug 16 17:53:59 mythfront1 kernel: [100593.507990] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Aug 16 17:53:59 mythfront1 kernel: [100593.507996] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 29 15 92 00 00 02 00
Aug 16 17:59:47 mythfront1 kernel: [100941.837143] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 16 17:59:47 mythfront1 kernel: [100941.837151] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Aug 16 17:59:47 mythfront1 kernel: [100941.837157] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Aug 16 17:59:47 mythfront1 kernel: [100941.837169] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 29 0f 00 00 00 40 00
Aug 16 17:59:47 mythfront1 kernel: [100941.837184] __ratelimit: 85 callbacks suppressed
Aug 16 17:59:47 mythfront1 kernel: [100941.918476] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 16 17:59:47 mythfront1 kernel: [100941.918483] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Aug 16 17:59:47 mythfront1 kernel: [100941.918489] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Aug 16 17:59:47 mythfront1 kernel: [100941.918501] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 29 11 c0 00 00 10 00
Aug 16 17:59:48 mythfront1 kernel: [100942.109881] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 16 17:59:48 mythfront1 kernel: [100942.109886] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Aug 16 17:59:48 mythfront1 kernel: [100942.109890] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Aug 16 17:59:48 mythfront1 kernel: [100942.109898] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 29 15 92 00 00 08 00
Aug 16 17:59:48 mythfront1 kernel: [100942.112544] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 16 17:59:48 mythfront1 kernel: [100942.112549] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Aug 16 17:59:48 mythfront1 kernel: [100942.112553] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Aug 16 17:59:48 mythfront1 kernel: [100942.112559] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 29 15 92 00 00 02 00
Aug 16 17:59:48 mythfront1 kernel: [100942.115166] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 16 17:59:48 mythfront1 kernel: [100942.115170] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Aug 16 17:59:48 mythfront1 kernel: [100942.115174] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Aug 16 17:59:48 mythfront1 kernel: [100942.115180] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 29 15 92 00 00 02 00
Aug 16 17:59:48 mythfront1 kernel: [100942.117960] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 16 17:59:48 mythfront1 kernel: [100942.117966] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Aug 16 17:59:48 mythfront1 kernel: [100942.117971] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Aug 16 17:59:48 mythfront1 kernel: [100942.117979] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 29 15 92 00 00 02 00
```

Can anyone point me in the right direction?

TIA!

---

