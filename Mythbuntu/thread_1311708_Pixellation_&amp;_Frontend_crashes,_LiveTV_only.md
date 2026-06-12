---
title: "Pixellation &amp; Frontend crashes, LiveTV only"
date: 2009-11-02
forum: Mythbuntu
---

### Post by SiHa on 2009-11-02
Fresh install of 9.10.

SD LiveTV (HD appears OK) pixellates and audio stutters terribly frontend crashes, and I get loads of this in the frontend log:

```
2009-11-02 21:13:38.886 AFD Error: Unknown audio decoding error                                                               
2009-11-02 21:13:48.683 [mp2 @ 0x46dc6c0]Header missing                                                                       
2009-11-02 21:13:48.683 AFD Error: Unknown audio decoding error                                                               
2009-11-02 21:14:01.483 [mp2 @ 0x46dc6c0]Header missing                                                                       
2009-11-02 21:14:01.484 AFD Error: Unknown audio decoding error                                                               
2009-11-02 21:14:04.684 [mp2 @ 0x46dc6c0]Header missing                                                                       
2009-11-02 21:14:04.684 AFD Error: Unknown audio decoding error                                                               
2009-11-02 21:14:11.326 [mp2 @ 0x46dc6c0]Header missing                                                                       
2009-11-02 21:14:11.326 AFD Error: Unknown audio decoding error                                                               
2009-11-02 21:14:14.552 [mp2 @ 0x46dc6c0]Header missing                                                                       
2009-11-02 21:14:14.552 AFD Error: Unknown audio decoding error                                                               
2009-11-02 21:14:17.778 [mp2 @ 0x46dc6c0]Header missing                                                                       
2009-11-02 21:14:17.778 AFD Error: Unknown audio decoding error                                                               
2009-11-02 21:14:33.527 [mp2 @ 0x46dc6c0]Header missing                                                                       
2009-11-02 21:14:33.527 AFD Error: Unknown audio decoding error                                                               
2009-11-02 21:14:50.307 [mp2 @ 0x46dc6c0]Header missing                                                                       
2009-11-02 21:14:50.308 AFD Error: Unknown audio decoding error                                                               
2009-11-02 21:14:56.810 [mp2 @ 0x46dc6c0]Header missing                                                                       
2009-11-02 21:14:56.810 AFD Error: Unknown audio decoding error                                                               
200
```

I watched for ~15 mins until the frontend silently exited (nothing in the frontend log or syslog), and there was lots of pixellation.

I pressed 'Record' just after starting to watch. And this is the strange bit: If I watch the recording, the picture is perfect, all I get in the log is the very occasional prebuffering pause with no visual glitch.

Using VDPAU slim(also happens with VDPAU normal). I'll try a non-VDPAU profile for SD tomorrow, but I'd be grateful if anyone else has any pointers.

TIA,

Simon

---

### Post by SiHa on 2009-11-04
Update:

Look like it's a segfault - didn't spot it before.

Syslog:```
Nov  4 20:12:51 frontend-desktop lircd-0.8.6[1216]: accepted new client on /var/run/lirc/lircd
Nov  4 20:15:48 frontend-desktop kernel: [39557.052085] mythfrontend.re[2671]: segfault at 0 ip 05cd2006 sp b31012f8 error 6 in libc-2.10.1.so[5c5d000+13e000]
Nov  4 20:15:48 frontend-desktop lircd-0.8.6[1216]: removed client
Nov  4 20:15:57 frontend-desktop lircd-0.8.6[1216]: accepted new client on /var/run/lirc/lircd
Nov  4 20:17:01 frontend-desktop CRON[2732]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  4 20:17:41 frontend-desktop kernel: [39669.842171] mythfrontend.re[2758]: segfault at 0 ip 07170006 sp ad90e2f8 error 6 in libc-2.10.1.so[70fb000+13e000]
Nov  4 20:17:41 frontend-desktop lircd-0.8.6[1216]: removed client
Nov  4 20:17:46 frontend-desktop lircd-0.8.6[1216]: accepted new client on /var/run/lirc/lircd
Nov  4 20:19:17 frontend-desktop kernel: [39766.271272] mythfrontend.re[2802]: segfault at 0 ip 021af006 sp b38832f8 error 6 in libc-2.10.1.so[213a000+13e000]

```
Mythfrontend.log:```
2009-11-04 20:18:37.489 TV: Attempting to change from None to Watching WatchingLiveTV
2009-11-04 20:18:37.495 MythContext: Connecting to backend server: 192.168.1.162:6543 (try 1 of 1)
2009-11-04 20:18:37.497 Using protocol version 50
2009-11-04 20:18:37.564 Spawning LiveTV Recorder -- begin
2009-11-04 20:18:38.986 Spawning LiveTV Recorder -- end
2009-11-04 20:18:39.012 We have a playbackURL(/var/lib/mythtv/livetv/2002_20091104201831.mpg) & cardtype(DUMMY)
2009-11-04 20:18:39.013 We have a RingBuffer
2009-11-04 20:18:39.065 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- begin
2009-11-04 20:18:39.117 NVP(0): Disabling Audio, params(-1,2,44100)
2009-11-04 20:18:39.234 FilterManager: Failed to load filter 'colorspace', no such filter exists
2009-11-04 20:18:39.237 OSD Theme Dimensions W: 1280 H: 720
2009-11-04 20:18:39.253 New DB connection, total: 3
2009-11-04 20:18:39.329 Connected to database 'mythconverg' at host: 192.168.1.162
2009-11-04 20:18:39.481 New DB connection, total: 4
2009-11-04 20:18:39.485 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end ok
2009-11-04 20:18:39.485 TV: Changing from None to Watching WatchingLiveTV
2009-11-04 20:18:39.485 TV: State is LiveTV & mctx == ctx
2009-11-04 20:18:39.489 OpenGLVideoSync()
2009-11-04 20:18:39.490 TV: UpdateOSDInput done
2009-11-04 20:18:39.490 TV: UpdateLCD done
2009-11-04 20:18:39.490 TV: ITVRestart done
2009-11-04 20:18:39.512 Connected to database 'mythconverg' at host: 192.168.1.162
2009-11-04 20:18:39.515 The realtime priority setting is not enabled.
2009-11-04 20:18:39.633 Video timing method: SGI OpenGL
2009-11-04 20:18:39.654 FilterManager: Failed to load filter 'colorspace', no such filter exists
2009-11-04 20:18:40.660 RingBuf(/var/lib/mythtv/livetv/2002_20091104201832.mpg): Waited 1.0 seconds for data to become available...
2009-11-04 20:18:40.660 Checking to see if there's a new livetv program to switch to..
2009-11-04 20:18:41.662 RingBuf(/var/lib/mythtv/livetv/2002_20091104201832.mpg): Waited 2.0 seconds for data to become available...
2009-11-04 20:18:41.663 Checking to see if there's a new livetv program to switch to..
2009-11-04 20:18:43.969 RingBuf(/var/lib/mythtv/livetv/2002_20091104201832.mpg): Waited 1.0 seconds for data to become available...
2009-11-04 20:18:43.969 Checking to see if there's a new livetv program to switch to..
2009-11-04 20:18:44.973 RingBuf(/var/lib/mythtv/livetv/2002_20091104201832.mpg): Waited 2.0 seconds for data to become available...
2009-11-04 20:18:44.973 Checking to see if there's a new livetv program to switch to..
2009-11-04 20:18:46.329 NVP(0): Forcing decode extra audio option on (Video method requires it).
2009-11-04 20:18:46.463 FilterManager: Failed to load filter 'colorspace', no such filter exists
2009-11-04 20:18:46.463 AFD: Opened codec 0xb20ecfb0, id(MPEG2VIDEO) type(Video)
2009-11-04 20:18:46.463 AFD: codec MP2 has 2 channels
2009-11-04 20:18:46.463 AFD: Opened codec 0xb267cf60, id(MP2) type(Audio)
2009-11-04 20:18:46.463 AFD: codec MP2 has 1 channels
2009-11-04 20:18:46.463 AFD: Opened codec 0xb1f82fb0, id(MP2) type(Audio)
2009-11-04 20:18:46.463 AFD: Opened codec 0xb2675ec0, id(DVB_SUBTITLE) type(Subtitle)
2009-11-04 20:18:46.537 Opening audio device 'hdmi'. ch 2(2) sr 48000
2009-11-04 20:18:46.537 Opening ALSA audio device 'hdmi'.
2009-11-04 20:18:46.599 NVP(0): Enabling Audio
Starting mythfrontend.real..
[CODE]
```[/CODE]

I can confirm that this only happens on Live TV on the remote frontend. FE on the BE server is fine, can watch Live TV for hours with no issue. So I assume from that that it's not a HDD throughput issue.

On the remote frontend, Live TV will segfault after at most 5 minutes. Watching a recording of the same show is fine.

While watching the LiveTV, the frontend log is littered with the above 'Unknown audio decoding error", each error coincides with a visual pixellation glitch. Watching a recording of the same show has none, and will not segfault.

I had assumed the segfault and audio error were connected, as the last entry in the frontend log was always the audio error, except for the last one, so maybe not?

Also, only seems to happen with SD DVB-T, HD DVB-S is fine.

I've tried, Enable/Disable:
Extra audio buffering
OpenGL Video Timing
Aggressive sound card buffering
Use real-time priority

Using non-VDPAU profile (CPU++, ffmpeg & XVideo)
Change recording profile to 'TV Only' - Audio & Video streams only.

Now what's got me really confused is that Live TV is a recording anyway. If I'm watching a show live, then press 'Record' Myth simply changes a database flag from LiveTV to Recording, so why does Live bomb and a recording is OK?????

I haved noticed that LiveTV does seem to take longer to buffer than it used to with my old 8.04 install (5-6s).

I really hope someone can help me with this. 0.22's great, but near unusable if LiveTV is not working.

Is there any more info I can provide? I'd do a backtrace if I knew how!

Edit: Looked at all logfiles with a last entry at the same time as the sefault (kern.log, message.log), but they just show the same segfault, nothing else.

---

### Post by utar on 2009-11-04
Are you using storage groups?

If this only happens on remote front ends it could be an issue with the streaming.  Just a guess though as I'm not running 0.22 yet, although I'm planning on installing this weekend.

I am interested in your progress though particular on the Nova.


Utar

---

### Post by pssturges on 2009-11-04
This sounds like a bug that's been around forever! See this thread [here.]("http://ubuntuforums.org/showthread.php?t=810310") Basically what happens is that a default playback profile is selected before signal lock is achieved and it doesn't change after. If you set up can play HD with that profile then all is good. If it can't...

Because you are not waiting for signal lock with recordings, the profile is set up correctly.

The work around I have been using is to create a custom profile and find settings that work well for HD. Set up the profile to use these settings for all content.

I hope that helps

Phil

---

### Post by SiHa on 2009-11-05
> **utar said:**
> Are you using storage groups?

If this only happens on remote front ends it could be an issue with the streaming.  Just a guess though as I'm not running 0.22 yet, although I'm planning on installing this weekend.

I am interested in your progress though particular on the Nova.
Utar

No, not using storage groups (not intentionally, anyway!).

I agree, it occurred to me last night after posting, that it might be a streaming issue. I have /var/lib/mythtv shared via nfs to my frontend, so, in theory it could be pulling the recordings from there (so not streaming), and that could be the difference between watching live and recorded. Before I came to work this morning, I did try checking the 'Always stream recordings from the backend' in an attempt to break recording playback and narrow down the problem. Unfortunately, the playback was perfect with no segfault! Tonight, I'll try unmounting the nfs share altogether, and see what happens.

Another thought that occurred: I'm sharing /var/lib/mythtv, as it seemed easier than individually sharing all the other subdirectories that have appeared in 0.22, most of which seem to be required for fanart etc. to display on the frontend.
But the Mythtv default nfs exports are just recordings, videos, music and pictures, or is this just a hangover from 0.21 that hasn't been corrected yet?
Is it possible that because my frontend can access, locally, var/lib/mythtv/livetv, this is somehow screwing things up?

As far as the Nova is concerned, I think I can now say with a fair degree of confidence, that a fresh install of 9.10(32bit) + 1.10 firmware is stable: No I2C errors since last Sunday.

[QUOTE=pssturges]This sounds like a bug that's been around forever![/QUOTE]
Thanks Phil.
Not sure this sounds the same though. My playback isn't stuttering, most of the time it's fine, just with the occasional glitch, that looks like signal interference every 30s-2m followed by a segfault after 5-10 mins. And, I'm using VDPAU slim, which is >0,0 = VDPAU. So it shouldn't make any difference at all what Myth thinks before it gains a signal lock, it should still use the same profile. I did try CPU++ which just uses ffmpeg regardless, but with no affect. Also, using VDPAU playing HD, my CPU is @ 18%, and with SD it's 9%. Essentially, I've already tried the fixes for this bug, but to no avail.

---

### Post by utar on 2009-11-05
> **SiHa said:**
> No, not using storage groups (not intentionally, anyway!).


My understanding is that storage groups are setup by default, so unless you have changed the backend settings you are probably using storage groups.

I guess a quick way to check if you are using storage groups would be to stop all nfs shares and see if your remote frontend still works.

Cheers for the feedback on the Nova, I'm going to install this weekend.


Utar

---

### Post by SiHa on 2009-11-05
> **utar said:**
> My understanding is that storage groups are setup by default, so unless you have changed the backend settings you are probably using storage groups.


Oh.

Thinking about it, that might explain why the .iso I tried to play the other day didn't work!
Better have a look then, cheers.

> **utar said:**
> 
I guess a quick way to check if you are using storage groups would be to stop all nfs shares and see if your remote frontend still works.

Yep, that's first on my list tonight. 
[QUOTE=Utar]Cheers for the feedback on the Nova, I'm going to install this weekend.
[/QUOTE]
Enjoy!

---

### Post by SiHa on 2009-11-05
Well. Wouldn't you know. I unmounted the nfs shares, and I can watch Live TV without the glitches or segfaults!

...and I can watch my videos, so I guess that confirms I'm using storage groups. Thanks Utar for the pointer.

Can't disable the storage groups for the moment, New Tricks is taping, I'll have a play over the weekend with disabling the storage groups and re-enabling the nfs shares to see if I can nail down exactly what combinaton causes the segfault. Then maybe I should file a bug.

---

