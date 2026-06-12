---
title: "frontend crashing"
date: 2009-05-17
forum: Mythbuntu
---

### Post by gator on 2009-05-17
frontend is crashing at least once a day when changing channel or selecting liveTV. Log shows.

WriteAudio: buffer underrun
mythfrontend.real: ../../src/xcb_io.c:176: process_responses: Assertion `!(req && current_request && !(((long) (req->sequence) - (long) (current_request)) <= 0))' failed

i have avernards repos (stable) enabled:-x:-x](*,)

Anyone else see this?
edit: just grabbed a new update 20573... fingers crossed...

my system is amd 5400X2 4GB ram, nvidia 9400GT - playback is smooth but top show mythfrontend at 119% (???)
vmstat shows - while watching tv in HD
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 2  0  17020 2492372  24128 713772    0    0   548   381  149   17 17 10 72  1
 2  0  17020 2482732  24128 723004    0    0     0  1980 5668 9433 30 34 36  1
 1  0  17020 2473260  24128 732324    0    0     0  1632 5636 9394 31 34 35  1
 1  0  17020 2463512  24128 741636    0    0     0  2015 5565 9375 31 34 35  0
35% idle - wtf

more crashes....

2009-05-19 11:46:11.352 AFD: codec MP3 has 2 channels
2009-05-19 11:46:11.353 AFD: Opened codec 0x7fd3340fd0e0, id(MP3) type(Audio)
2009-05-19 11:46:11.384 Opening audio device 'default'. ch 2(2) sr 48000
2009-05-19 11:46:11.384 Opening ALSA audio device 'default'.
2009-05-19 11:46:11.429 Mixer unable to find control Master
2009-05-19 11:46:11.429 Mixer unable to find control Master
2009-05-19 11:46:11.431 NVP: Enabling Audio
2009-05-19 11:46:21.451 NVP: prebuffering pause
2009-05-19 11:46:21.508 WriteAudio: buffer underrun
2009-05-19 11:46:24.887 NVP: Prebuffer wait timed out 10 times.
2009-05-19 11:46:25.416 AFD: Opened codec 0x160dee60, id(MPEG2VIDEO) type(Video)
2009-05-19 11:46:25.416 AFD: codec AC3 has 6 channels
2009-05-19 11:46:25.418 AFD: Opened codec 0x100f8b60, id(AC3) type(Audio)
2009-05-19 12:00:02.518 [ac3 @ 0x7fd3597ffed0]frame CRC mismatch
2009-05-19 12:08:58.231 NVP: prebuffering pause
2009-05-19 12:08:58.323 WriteAudio: buffer underrun
mythfrontend.real: Fatal IO error: client killed

i will investigate my sound system...

---

### Post by gator on 2009-05-24
did lots of updates
nvidia 180.60
mythtv 20600

still happy except for these random crashes when selecting liveTV.


2009-05-24 20:36:58.187 TV: Attempting to change from None to WatchingLiveTV
2009-05-24 20:36:58.189 Using protocol version 40
2009-05-24 20:36:59.607 DPMS Deactivated 
2009-05-24 20:36:59.949 NVP: Disabling Audio, params(-1,2,44100)
2009-05-24 20:37:00.745 OSD Theme Dimensions W: 640 H: 480
2009-05-24 20:37:01.716 TV: Changing from None to WatchingLiveTV
2009-05-24 20:37:01.767 The realtime priority setting is not enabled.
2009-05-24 20:37:01.904 OpenGLVideoSync()
2009-05-24 20:37:02.211 Video timing method: SGI OpenGL
mythfrontend.real: Fatal IO error: client killed

After a crash i restart the frontend and select live tv again and it works
2009-05-24 20:43:43.593 TV: Attempting to change from None to WatchingLiveTV
2009-05-24 20:43:43.594 Using protocol version 40
2009-05-24 20:43:44.910 DPMS Deactivated 
2009-05-24 20:43:44.923 NVP: Disabling Audio, params(-1,2,44100)
2009-05-24 20:43:45.692 OSD Theme Dimensions W: 640 H: 480
2009-05-24 20:43:46.528 TV: Changing from None to WatchingLiveTV
2009-05-24 20:43:46.535 New DB connection, total: 3
2009-05-24 20:43:46.536 New DB connection, total: 4
2009-05-24 20:43:46.539 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:43:46.542 The realtime priority setting is not enabled.
2009-05-24 20:43:46.545 Connected to database 'mythconverg' at host: localhost
2009-05-24 20:43:46.637 OpenGLVideoSync()
2009-05-24 20:43:46.706 Video timing method: SGI OpenGL
2009-05-24 20:43:48.892 AFD: Opened codec 0x10516cc0, id(MPEG2VIDEO) type(Video)
2009-05-24 20:43:48.893 AFD: codec AC3 has 6 channels
2009-05-24 20:43:48.895 AFD: Opened codec 0x105161d0, id(AC3) type(Audio)
2009-05-24 20:43:49.118 Opening audio device 'default'. ch 2(2) sr 48000
2009-05-24 20:43:49.232 Opening ALSA audio device 'default'.
2009-05-24 20:43:49.325 Mixer unable to find control Master
2009-05-24 20:43:49.325 Mixer unable to find control Master
2009-05-24 20:43:49.328 NVP: Enabling Audio
2009-05-24 20:44:08.709 XMLParse::LoadTheme using /usr/share/mythtv/themes/blootube-wide/ui.xml
2009-05-24 20:44:29.293 NVP: prebuffering pause
2009-05-24 20:44:29.346 WriteAudio: buffer underrun
2009-05-24 20:44:32.685 NVP: Prebuffer wait timed out 10 times.
2009-05-24 20:44:33.093 WriteAudio: buffer underrun
2009-05-24 20:44:33.149 WriteAudio: buffer underrun
2009-05-24 20:44:33.236 WriteAudio: buffer underrun
2009-05-24 20:44:33.283 WriteAudio: buffer underrun
2009-05-24 20:44:33.461 AFD: Opened codec 0x7f1544fb99e0, id(MPEG2VIDEO) type(Video)
2009-05-24 20:44:33.461 AFD: codec MP3 has 2 channels
2009-05-24 20:44:33.461 AFD: Opened codec 0x7f1544fbcdf0, id(MP3) type(Audio)
2009-05-24 20:45:27.233 [mpeg2video @ 0x7f1566d27ed0]skipped MB in I frame at 20 31
2009-05-24 20:45:27.237 [mpeg2video @ 0x7f1566d27ed0]Warning MVs not available

dmesg shows...

[53478.950379] mythfilldatabas[22119]: segfault at 187ecd0 ip 000000000187ecd0 sp 00007f0eec9bed78 error 15
[60682.615400] mythfilldatabas[28441]: segfault at 2535400 ip 0000000002535400 sp 00007fa257594d78 error 15
[64286.575529] mythfilldatabas[800]: segfault at b7d450 ip 0000000000b7d450 sp 00007f8796cc3d78 error 15
[89495.963591] mythfilldatabas[24346]: segfault at 10360d0 ip 00000000010360d0 sp 00007f573eb16d78 error 15
[111106.824054] mythfilldatabas[11396]: segfault at 49 ip 00007f62dda4eee7 sp 00007fffe6726ea0 error 4 in libmythtv-0.21.so.0.21.0[7f62dd835000+a73000]
[123227.645277] mythfrontend.re[9256]: segfault at 28 ip 00007f5d3bbaf0e8 sp 00007fff49323700 error 4 in libqt-mt.so.3.3.8[7f5d3b835000+80d000]


please someone help

---

### Post by ian dobson on 2009-05-24
Hi,

Have you configured the frontend to use VDPAU (avernards repos)?

In you log file I see:-
AFD: Opened codec 0x160dee60, id(MPEG2VIDEO) type(Video)

and on my VDPAU enabled frontend I see:-
AFD: Opened codec 0x7f94969963c0, id(MPEGVIDEO_VDPAU) type(Video)

What graphic card to you have in your frontend?

Regards
Ian Dobson

---

### Post by gator on 2009-05-24
thanks for your reply i have a msi 9400gt - if i use vdpau decoder i get coloured blocks which looks like bad reception, i'm sure i read somewhere that its a known problem,the blocks only appear with mpeg2 as blu ray rips look and play amazing so ive switched to ffmpeg decoder and vdpau with temporalX2 deinterlacer. The frontend crashes the same with opengl and kernelX2HW deinterlacer. 

[123227.645277] mythfrontend.re[9256]: segfault at 28 ip 00007f5d3bbaf0e8 sp 00007fff49323700 error 4 in libqt-mt.so.3.3.8[7f5d3b835000+80d000]

this looks bad, libqt-mt.so.3.3.8, maybe something happened with the upgrade from 8.10
i'm lost on what to try next

---

### Post by ian dobson on 2009-05-24
Hi,

Strange. I'm using VDPAU/GT 9300 and can playback MPEG2 without any problems :)

Maybe try using VDPAU but using different deinterlacer or maybe a different acceleration (Xv-Blt?).

Regards
Ian Dobson

---

### Post by gator on 2009-05-30
ok, i seem to have solved this problem - i first did more updates moving to the nvidia 185 driver along with more mythtv updates. The frontend was crashing just the same, oneHD seemed to crash more than other stations. I did a search for this error '/src/xcb_io.c:176: process_responses: Assertion' and found a few threads that suggested that i disable the 'openGL sync to vblank' . This seems to have fixed it - no more crashing and luckily no tearing. I still have a few other issues before its perfect.

1. vdpau decoding mpeg2 still has coloured blocks like bad reception switching to standard(ffmpeg) fixes this.

2. top still shows frontend at over 100% (???) - but playback is smooth
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1657 steve     20   0 1016m 491m  64m S  108 12.6 332:39.46 mythfrontend.re    
 3100 mythtv    20   0  729m  72m 5908 S   29  1.9 252:59.51 mythbackend        
 3428 root      20   0  906m 293m  17m S    4  7.5   9:56.28 Xorg               
29795 steve     20   0 19116 1332  988 R    1  0.0   0:00.22 top                
   32 root      15  -5     0    0    0 S    0  0.0   0:32.03 kswapd0            
 2131 root      15  -5     0    0    0 S    0  0.0   0:08.96 xfsdatad/1         
 2904 mysql     20   0  266m  54m 3372 S    0  1.4  20:34.26 mysqld        

vmstat 5 shows a different story

 procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 5  0  10952  22692   7036 2800532    0    0   273   223   36  127 14  6 79  1
 2  0  10952  23224   7036 2800052    0    0    51  1151 4514 4970 34  4 62  0
 1  0  10952  26500   7044 2796844    0    0    51   919 4557 4887 33  4 62  0
 1  0  10952  21936   7052 2801260    0    0    26   739 4487 4721 32  4 64  0

64% idle - maybe i'm just not reading it right
strange.

3. because of jerky panning with bluray and ntsc video i included a refresh definition file Utilities/Setup -> Setup -> Appearance and check 
'Separate video modes for GUI and TV Playback'. This works well and my tv adjusts to 23.97fps for bluray and back to 50fps for tv but now the mouse pointer appears - i have checked ' hide mouse pointer'. Any ideas ? 
edit: My mate has the same tv ( panasonic 48 inch plasma ) and the same definition file on mythbuntu 8.10 - the mouse does not show on his.
There is a thread about this here it looks like a 9.04 problem [http://ubuntuforums.org/showthread.php?p=7374531#post7374531](http://ubuntuforums.org/showthread.php?p=7374531#post7374531)
Thanks again

---

