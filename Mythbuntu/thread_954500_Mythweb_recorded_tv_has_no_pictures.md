---
title: "Mythweb: recorded tv has no pictures"
date: 2008-10-21
forum: Mythbuntu
---

### Post by mark467 on 2008-10-21
Mythweb: recorded tv has no pictures...
In mythweb under recorded programs the box to the left that is supposed to have a picture of the show has only a colored box.
My previous myth box had a screen cap there.

---

### Post by mratomic on 2008-10-21
I noticed this too on a recording from Sunday.
I think it happened to me because I was accessing mythweb during a time which the CPU was struggling.  All the other icons showed up for other programs recorded at other times.

---

### Post by ian dobson on 2008-10-21
Hi,

Myth tries to create a "preview" picture during a recording, sometimes it just doesn't work and you get "empty" previews.

I've seen it afew times on my backend and usually just waiting abit and trying again solves it, as if a preview doesn't exist mythweb tells the backend to try and create a new preview.

Regards
Ian Dobson

---

### Post by mark467 on 2008-10-21
Ok. I changed my transcoding from rtjpeg to mpg4 today and all the new recordings have the pictures and the others still dont. i guess it cant pull pics from default transcoding

---

### Post by 4dognight on 2008-10-21
> **mark467 said:**
> Mythweb: recorded tv has no pictures...
In mythweb under recorded programs the box to the left that is supposed to have a picture of the show has only a colored box.
My previous myth box had a screen cap there.

Does the file actually exist for the recording? Does it show a file size  or a 'B' in the column heading for File Size?

---

### Post by funkydan2 on 2008-10-23
I've got this same problem (see [this thread]("http://ubuntuforums.org/showthread.php?t=951346")) and the recording works perfectly through the full mythtv frontend, it just seems to be a problem on MythWeb.

On my machine, I think it's a problem that's only started since a codec package was updated through the update manager, *but I don't remember what package that was*.

Any help would be greatly appreciated, because I can now no longer use the mythweb flash based player to watch recorded shows, which had been really useful in the past.

---

### Post by ian dobson on 2008-10-23
Hi,

What do you see in the backend log? On my box when I force  MythTV/MythWeb I see:-

```
2008-10-23 09:08:01.419 New DB connection, total: 2
2008-10-23 09:08:01.420 Connected to database 'mythconverg' at host: localhost
2008-10-23 09:08:01.421 Current Schema Version: 1214
2008-10-23 09:08:01.578 Preview: Grabbed preview '/data/mythtv/recordings/32434_20080919191000.nuv' 720x576@159s
2008-10-23 09:08:01.756 Using runtime prefix = /usr
2008-10-23 09:08:41.966 New DB connection, total: 2
2008-10-23 09:08:41.967 Connected to database 'mythconverg' at host: localhost
2008-10-23 09:08:41.969 Current Schema Version: 1214
2008-10-23 09:08:42.273 AFD: Opened codec 0x8db470, id(MPEG2VIDEO) type(Video)
2008-10-23 09:08:42.273 AFD: codec MP3 has 2 channels
2008-10-23 09:08:42.274 AFD: Opened codec 0x8dbab0, id(MP3) type(Audio)
2008-10-23 09:08:42.275 AFD: codec MP3 has 2 channels
2008-10-23 09:08:42.275 AFD: Opened codec 0x8dc0f0, id(MP3) type(Audio)
2008-10-23 09:08:42.276 AFD: Opened codec 0x8dcdf0, id(DVB_SUBTITLE) type(Subtitle)
2008-10-23 09:08:42.415 Preview: Grabbed preview '/data/mythtv/recordings/35003_20080721200900.mpg' 720x576@159s
```

Regards
Ian Dobson

---

### Post by funkydan2 on 2008-10-24
Hi Ian,

What do you mean by 'force MythTV/MythWeb'?

I've had a look at your log file, and mine, and I can't see any relevant error messages.  I still don't know the cause of the problem, but it seems that the appropriate image file is not ending up in '*mythweb directory*/data/cache/'.

DS

---

### Post by funkydan2 on 2008-10-25
This isn't a real solution, but I upgraded my myth box to Intrepid today, and now it's working.  I still think the cause of the problem was a bug in a codec package, but that can't be tested anymore.

DS

---

### Post by ian dobson on 2008-10-25
Hi,

Your can force mythbackend to regenerate the preview images with the command

mythbackend --generate-preview --chanid XXX --starttime YYY

Sorry that I didn't finish the sentence, Doing 2 things at once isn't always the best idea.

Regards
Ian Dobson

---

### Post by funkydan2 on 2008-10-26
Actually, I think that this is the same problem as [http://ubuntuforums.org/showthread.php?t=959211](http://ubuntuforums.org/showthread.php?t=959211) and is actually to do with the way that PHP5 in Hardy handles daylight saving time and *not* to do with codecs.

I'm going to go and participate in that thread...

---

### Post by EasyRiderOnTheStorm on 2008-11-17
I have no idea what this is related to, but I seem to have the same problem. Namely, all the generated preview .png files (yes, they are present) are just coloured 1x1 pixel images, for all and every recording, no matter how many times I regenerate them. Mythbackend seems to think that all is ok - all I get is stuff like: ```
Preview: Grabbed preview '/rec/recordings/1_20081116194500.nuv' 480x576@30s
```
For whatever reason, the preview grabber is obviously reverting to a 1x1 block having the appropriate colour for the **type** of the recording it's generating the preview for, instead of an actual frame from the recording. Any idea why it would do that...?

Oh, one more thing - On a single occasion I **did** get a perfect preview of a recording - after I transcoded one from the original RTJpeg nuv to an MPEG4 nuv. Just commflagging does not have the same result, previews stay 1x1.

---

### Post by EasyRiderOnTheStorm on 2008-11-19
It's indeed a selective failure. I test-recorded a few minutes of video in the default RTJpeg .nuv (which immediately failed to generate anything other then the weird 1 pixel default thumbnail and another 75x100 single-color mythweb thumbnail), then transcoded it to an MPEG4 .nuv. Sure enough, it immediately sprouted a 319x240 and a 75x100 picture-perfect preview thumbnails. Below are the verbose ( "-v most" ) logs of mythbackend for a successful generate-preview run...

```
2008-11-19 04:11:31.810 Using runtime prefix = /usr
2008-11-19 04:11:31.852 Empty LocalHostName.
2008-11-19 04:11:31.853 Using localhost value of mythbox
2008-11-19 04:11:31.895 MCP::DefaultUPnP() - No default UPnP backend
2008-11-19 04:11:32.269 New DB connection, total: 1
2008-11-19 04:11:32.309 Connected to database 'mythconverg' at host: localhost
2008-11-19 04:11:32.311 Closing DB connection named 'DBManager0'
2008-11-19 04:11:32.312 Connected to database 'mythconverg' at host: localhost
2008-11-19 04:11:32.337 New DB connection, total: 2
2008-11-19 04:11:32.338 Connected to database 'mythconverg' at host: localhost
2008-11-19 04:11:32.381 Current Schema Version: 1214
2008-11-19 04:11:32.411 New DB connection, total: 3
2008-11-19 04:11:32.414 Connected to database 'mythconverg' at host: localhost
2008-11-19 04:11:32.453 RingBuf(546_20081119035501.nuv): OpenFile(546_20081119035501.nuv, 0)
2008-11-19 04:11:32.493 RingBuf(546_20081119035501.nuv): CalcReadAheadThresh(3086380096 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2008-11-19 04:11:32.556 detectInterlace(Ignore Scan, Interlaced Scan, 25, 576) ->Interlaced Scan
2008-11-19 04:11:32.583 RingBuf(546_20081119035501.nuv): CalcReadAheadThresh(3086116548 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2008-11-19 04:11:32.670 VDP: Accepting: cmp(<= 720 576,> 0 0) dec(ffmpeg) cpus(1) skiploop(enabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(none,none) filt()
2008-11-19 04:11:32.670 VDP: Rejecting: cmp(<= 1280 720,> 720 576) dec(xvmc) cpus(1) skiploop(disabled) rend(xvmc-blit) osd(opengl) osdfade(enabled) deint(bobdeint,onefield) filt()
			OSD Renderer opengl is not supported w/renderer xvmc-blit (supported: chromakey,chromakey,ia44blend)
2008-11-19 04:11:32.670 VDP: Accepting: cmp(<= 1280 720,> 720 576) dec(libmpeg2) cpus(1) skiploop(disabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(bobdeint,onefield) filt()
2008-11-19 04:11:32.670 VDP: Accepting: cmp(> 0 0) dec(xvmc) cpus(1) skiploop(enabled) rend(xvmc-blit) osd(ia44blend) osdfade(disabled) deint(bobdeint,onefield) filt()
2008-11-19 04:11:32.671 VDP: Accepting: cmp(> 0 0) dec(libmpeg2) cpus(1) skiploop(disabled) rend(xv-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2008-11-19 04:11:32.671 VDP: LoadBestPreferences(2048x2048, 0)
2008-11-19 04:11:32.671 VDP: LoadBestPreferences(2048x2048, 60)
2008-11-19 04:11:32.681 VideoOutputNull()
2008-11-19 04:11:32.681 VDP: LoadBestPreferences(480x576, 60)
2008-11-19 04:11:32.681 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2008-11-19 04:11:32.681 Video Rect    left: 0, top: 0, width: 480, height: 576, aspect: 1.33333
2008-11-19 04:11:32.682 Created data @0x83107e0->0x8375be2
2008-11-19 04:11:32.682 Created data @0x8375c50->0x83db052
2008-11-19 04:11:32.682 Created data @0x83db0c0->0x84404c2
2008-11-19 04:11:32.682 Created data @0x8440530->0x84a5932
2008-11-19 04:11:32.690 Created data @0x84a59a0->0x850ada2
2008-11-19 04:11:32.690 Created data @0x850ae10->0x8570212
2008-11-19 04:11:32.690 Created data @0x8570280->0x85d5682
2008-11-19 04:11:32.691 Created data @0x85d56f0->0x863aaf2
2008-11-19 04:11:32.691 Created data @0x863ab60->0x869ff62
2008-11-19 04:11:32.691 Created data @0x869ffd0->0x87053d2
2008-11-19 04:11:32.691 Created data @0x8705440->0x876a842
2008-11-19 04:11:32.691 Created data @0x876a8b0->0x87cfcb2
2008-11-19 04:11:32.691 Created data @0x87cfd20->0x8835122
2008-11-19 04:11:32.691 Created data @0x8835190->0x889a592
2008-11-19 04:11:32.691 Created data @0x889a600->0x88ffa02
2008-11-19 04:11:32.691 Created data @0x88ffa70->0x8964e72
2008-11-19 04:11:32.691 Created data @0x8964ee0->0x89ca2e2
2008-11-19 04:11:32.691 Created data @0x89ca350->0x8a2f752
2008-11-19 04:11:32.692 Created data @0x8a2f7c0->0x8a94bc2
2008-11-19 04:11:32.692 Created data @0x8a94c30->0x8afa032
2008-11-19 04:11:32.692 Created data @0x8afa0a0->0x8b5f4a2
2008-11-19 04:11:32.692 Created data @0x8b5f510->0x8bc4912
2008-11-19 04:11:32.692 Created data @0x8bc4980->0x8c29d82
2008-11-19 04:11:32.692 Created data @0x8c29df0->0x8c8f1f2
2008-11-19 04:11:32.692 Created data @0x8c8f260->0x8cf4662
2008-11-19 04:11:32.692 Created data @0x8cf46d0->0x8d59ad2
2008-11-19 04:11:32.692 Created data @0x8d59b40->0x8dbef42
2008-11-19 04:11:32.693 Created data @0x8dbefb0->0x8e243b2
2008-11-19 04:11:32.693 Created data @0x8e24420->0x8e89822
2008-11-19 04:11:32.693 Created data @0x8e89890->0x8eeec92
2008-11-19 04:11:32.693 Created data @0x8eeed00->0x8f54102
2008-11-19 04:11:32.693 Created data @0x8f54170->0x8fb9572
2008-11-19 04:11:32.718 VDP: SetVideoRenderer(null)
2008-11-19 04:11:32.718 VDP: Old preferences: rend(xv-blit) osd(softblend) deint(none,none) filt()
2008-11-19 04:11:32.719 VDP: New preferences: rend(null) osd(softblend) deint(none,none) filt()
2008-11-19 04:11:32.719 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2008-11-19 04:11:32.719 Video Rect    left: 0, top: 0, width: 480, height: 576, aspect: 1.33333
2008-11-19 04:11:32.720 NVP: LoadFilters(''..) -> 0
2008-11-19 04:11:32.720 NVP: ClearAfterSeek(1)
2008-11-19 04:11:32.871 Dec: DoFastForward(898 (0), do discard frames)
2008-11-19 04:11:32.871 NVD: SeekReset(870, 0, do flush, do discard)
2008-11-19 04:11:32.871 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2008-11-19 04:11:32.872 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-11-19 04:11:32.872 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2008-11-19 04:11:32.872 NVP: ClearAfterSeek(0)
2008-11-19 04:11:32.917 ~VideoOutputNull()
2008-11-19 04:11:32.918 Preview: Grabbed preview '546_20081119035501.nuv' 480x576@30s
2008-11-19 04:11:33.271 Preview: Saved preview '546_20081119035501.nuv.png' 319x240

```

...and another, unsuccessful one (1 px result), for a different .nuv...

```
2008-11-19 04:11:56.801 Using runtime prefix = /usr
2008-11-19 04:11:56.802 Empty LocalHostName.
2008-11-19 04:11:56.802 Using localhost value of mythbox
2008-11-19 04:11:56.812 MCP::DefaultUPnP() - No default UPnP backend
2008-11-19 04:11:56.829 New DB connection, total: 1
2008-11-19 04:11:56.834 Connected to database 'mythconverg' at host: localhost
2008-11-19 04:11:56.836 Closing DB connection named 'DBManager0'
2008-11-19 04:11:56.837 Connected to database 'mythconverg' at host: localhost
2008-11-19 04:11:56.839 New DB connection, total: 2
2008-11-19 04:11:56.840 Connected to database 'mythconverg' at host: localhost
2008-11-19 04:11:56.850 Current Schema Version: 1214
2008-11-19 04:11:56.881 New DB connection, total: 3
2008-11-19 04:11:56.882 Connected to database 'mythconverg' at host: localhost
2008-11-19 04:11:56.904 RingBuf(1_20081116194500.nuv): OpenFile(1_20081116194500.nuv, 0)
2008-11-19 04:11:56.961 RingBuf(1_20081116194500.nuv): CalcReadAheadThresh(3086601280 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2008-11-19 04:11:56.997 detectInterlace(Ignore Scan, Interlaced Scan, 25, 576) ->Interlaced Scan
2008-11-19 04:11:57.015 RingBuf(1_20081116194500.nuv): CalcReadAheadThresh(3086337732 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2008-11-19 04:11:57.021 VDP: Accepting: cmp(<= 720 576,> 0 0) dec(ffmpeg) cpus(1) skiploop(enabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(none,none) filt()
2008-11-19 04:11:57.022 VDP: Rejecting: cmp(<= 1280 720,> 720 576) dec(xvmc) cpus(1) skiploop(disabled) rend(xvmc-blit) osd(opengl) osdfade(enabled) deint(bobdeint,onefield) filt()
			OSD Renderer opengl is not supported w/renderer xvmc-blit (supported: chromakey,chromakey,ia44blend)
2008-11-19 04:11:57.022 VDP: Accepting: cmp(<= 1280 720,> 720 576) dec(libmpeg2) cpus(1) skiploop(disabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(bobdeint,onefield) filt()
2008-11-19 04:11:57.022 VDP: Accepting: cmp(> 0 0) dec(xvmc) cpus(1) skiploop(enabled) rend(xvmc-blit) osd(ia44blend) osdfade(disabled) deint(bobdeint,onefield) filt()
2008-11-19 04:11:57.022 VDP: Accepting: cmp(> 0 0) dec(libmpeg2) cpus(1) skiploop(disabled) rend(xv-blit) osd(chromakey) osdfade(disabled) deint(bobdeint,onefield) filt()
2008-11-19 04:11:57.023 VDP: LoadBestPreferences(2048x2048, 0)
2008-11-19 04:11:57.023 VDP: LoadBestPreferences(2048x2048, 60)
2008-11-19 04:11:57.033 VideoOutputNull()
2008-11-19 04:11:57.033 VDP: LoadBestPreferences(480x576, 60)
2008-11-19 04:11:57.033 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2008-11-19 04:11:57.033 Video Rect    left: 0, top: 0, width: 480, height: 576, aspect: 1.33333
2008-11-19 04:11:57.033 Created data @0x83227f0->0x8387bf2
2008-11-19 04:11:57.034 Created data @0x8387c60->0x83ed062
2008-11-19 04:11:57.034 Created data @0x83ed0d0->0x84524d2
2008-11-19 04:11:57.034 Created data @0x84525c0->0x84b79c2
2008-11-19 04:11:57.034 Created data @0x84b7a20->0x851ce22
2008-11-19 04:11:57.034 Created data @0x851cfa0->0x85823a2
2008-11-19 04:11:57.034 Created data @0x8582400->0x85e7802
2008-11-19 04:11:57.034 Created data @0x85e7870->0x864cc72
2008-11-19 04:11:57.035 Created data @0x864cce0->0x86b20e2
2008-11-19 04:11:57.035 Created data @0x86b2380->0x8717782
2008-11-19 04:11:57.035 Created data @0x87177e0->0x877cbe2
2008-11-19 04:11:57.035 Created data @0x877cc50->0x87e2052
2008-11-19 04:11:57.035 Created data @0x87e20c0->0x88474c2
2008-11-19 04:11:57.035 Created data @0x8847530->0x88ac932
2008-11-19 04:11:57.035 Created data @0x88ac9a0->0x8911da2
2008-11-19 04:11:57.035 Created data @0x8911e10->0x8977212
2008-11-19 04:11:57.035 Created data @0x8977280->0x89dc682
2008-11-19 04:11:57.035 Created data @0x89dcb60->0x8a41f62
2008-11-19 04:11:57.036 Created data @0x8a41fc0->0x8aa73c2
2008-11-19 04:11:57.036 Created data @0x8aa7430->0x8b0c832
2008-11-19 04:11:57.036 Created data @0x8b0c8a0->0x8b71ca2
2008-11-19 04:11:57.036 Created data @0x8b71d10->0x8bd7112
2008-11-19 04:11:57.036 Created data @0x8bd7180->0x8c3c582
2008-11-19 04:11:57.036 Created data @0x8c3c5f0->0x8ca19f2
2008-11-19 04:11:57.036 Created data @0x8ca1a60->0x8d06e62
2008-11-19 04:11:57.036 Created data @0x8d06ed0->0x8d6c2d2
2008-11-19 04:11:57.036 Created data @0x8d6c340->0x8dd1742
2008-11-19 04:11:57.036 Created data @0x8dd17b0->0x8e36bb2
2008-11-19 04:11:57.037 Created data @0x8e36c20->0x8e9c022
2008-11-19 04:11:57.037 Created data @0x8e9c090->0x8f01492
2008-11-19 04:11:57.037 Created data @0x8f01500->0x8f66902
2008-11-19 04:11:57.037 Created data @0x8f66970->0x8fcbd72
2008-11-19 04:11:57.074 VDP: SetVideoRenderer(null)
2008-11-19 04:11:57.074 VDP: Old preferences: rend(xv-blit) osd(softblend) deint(none,none) filt()
2008-11-19 04:11:57.075 VDP: New preferences: rend(null) osd(softblend) deint(none,none) filt()
2008-11-19 04:11:57.075 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2008-11-19 04:11:57.075 Video Rect    left: 0, top: 0, width: 480, height: 576, aspect: 1.33333
2008-11-19 04:11:57.076 NVP: LoadFilters(''..) -> 0
2008-11-19 04:11:57.076 NVP: ClearAfterSeek(1)
2008-11-19 04:11:57.175 Dec: DoFastForward(898 (0), do discard frames)
2008-11-19 04:11:57.175 NVD: SeekReset(870, 0, do flush, do discard)
2008-11-19 04:11:57.175 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2008-11-19 04:11:57.176 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-11-19 04:11:57.176 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2008-11-19 04:11:57.176 NVP: ClearAfterSeek(0)
2008-11-19 04:11:57.221 ~VideoOutputNull()
2008-11-19 04:11:57.222 Preview: Grabbed preview '1_20081116194500.nuv' 480x576@30s
2008-11-19 04:11:57.270 Preview: Saved preview '1_20081116194500.nuv.png' 1x1

```

The weirdest thing is, they are perfectly identical except for the timestamps, filenames/sizes, the "created data..." parts, and the ending lines - a 319x240 .png vs. a 1x1 one. 
No explanation as to why. Any ideas anyone...? :(

---

### Post by EasyRiderOnTheStorm on 2008-11-23
...nobody? Any ideas?

---

### Post by EasyRiderOnTheStorm on 2008-12-02
...bump... 
...nobody has any ideas at all? :(

---

### Post by ian dobson on 2008-12-03
Hi,

What happens if you try and manualy force mythbackend to generate a thumb nail using the --generate-preview command line option for mythbackend.

Regards
Ian Dobson

---

### Post by EasyRiderOnTheStorm on 2008-12-03
> **ian dobson said:**
> Hi,

What happens if you try and manualy force mythbackend to generate a thumb nail using the --generate-preview command line option for mythbackend.

Regards
Ian Dobson

Please see three posts up. Those logs are from a successful run of "mythbackend --generate-preview" (on an MPEG4 nuv) and an unsuccessful one (on a RTJPEG nuv). This distinction by content holds true ever since then.

Regards,
EasyRider

---

