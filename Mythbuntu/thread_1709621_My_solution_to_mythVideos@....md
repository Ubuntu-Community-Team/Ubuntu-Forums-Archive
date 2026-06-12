---
title: "My solution to myth://Videos@..."
date: 2011-03-18
forum: Mythbuntu
---

### Post by kcaj on 2011-03-18
For some time now I have been having a problem playing videos with mythbuntu 10.10 and mythtv fixes/0.24. The video starts out playing fine for about 30 seconds and then begins stuttering. From that point on the video is not watchable. However, mplayer plays the file just fine but has to be called from a command line.

Using mplayer as the player in the setup doesn't work because the file name passed is 'myth://Videos@x.x.x.x:6543/DIR/FILE' which mplayer can't understand.

To solve the problem I wrote a small program that breaks up that string and substitutes the true directory path to the file and then calls mplayer with the proper filename.

This works just fine and I can now watch movies without the stuttering.

---

### Post by williammanda on 2011-03-18
Have you tried to supply any information to the forum ie log files, computer hardware, etc... to solve the existing issue?

---

### Post by kcaj on 2011-03-19
I have been to the site that reports and tracks bugs. The problem has  been reported and looking at the example logs that were uploaded I could  not add anything new. I've tried numerous suggestions found here and on  other sites with no luck.

Both mplayer and vlc play videos  flawlessly and mplayer works seamlessly with this solution. After nearly  4 months of searching, reading bug reports and forum posts I'm anxious  to put this box on my main TV which will replace a 0.21 box.

Sorry if I'm stepping on any toes...

---

### Post by williammanda on 2011-03-19
If you haven't posted the information about your issue here...please do so. This is a very active and experienced group. Your issue maybe someone else's issue.

---

### Post by kcaj on 2011-03-19
Okay, so the problem is mythtv will play some videos fine and others play for about 30 seconds before beginning the stuttering, Here is the front end log from a video that plays correctly:

```

2011-03-09 15:13:46.706 TV: Attempting to change from None to WatchingVideo
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
2011-03-09 15:13:47.300 VDPAU Error: Error at mythrender_vdpau.cpp:1486 (#1, Unknown)
2011-03-09 15:13:47.300 VDPAU Error: Failed to create VDPAU device.
2011-03-09 15:13:47.300 VDPAU Error: No VDPAU device
2011-03-09 15:13:47.300 VDPAU: Failed to create dummy device.
2011-03-09 15:13:47.301 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-03-09 15:13:47.301 AFD: Opened codec 0x7f9a8c2e7cc0, id(MPEG4) type(Video)
2011-03-09 15:13:47.301 AFD: codec MP3 has 2 channels
2011-03-09 15:13:47.301 AFD: Opened codec 0x7f9a8c2e85c0, id(MP3) type(Audio)
2011-03-09 15:13:47.420 AO: Opening audio device 'hdmi:CARD=HDMI,DEV=0' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2011-03-09 15:13:47.460 AudioPlayer: Enabling Audio
2011-03-09 15:13:47.484 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 1280 x 720
YadifDeint: Using existing thread.
2011-03-09 15:13:47.567 Player(9): Video timing method: USleep with busy wait
2011-03-09 15:13:47.568 TV: Changing from None to WatchingVideo
2011-03-09 15:13:47.658 VideoOutput: Created YV12 OSD.
2011-03-09 15:15:54.858 Marking recording as unwatched
2011-03-09 15:15:54.888 TV: Attempting to change from WatchingVideo to None

2011-03-09 15:15:54.930 TV: Changing from WatchingVideo to None

```Then here is the log from one that does not play correctly:

```
2011-03-09 15:12:55.736 TV: Attempting to change from None to WatchingVideo
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
2011-03-09 15:12:56.679 VDPAU Error: Error at mythrender_vdpau.cpp:1486 (#1, Unknown)
2011-03-09 15:12:56.679 VDPAU Error: Failed to create VDPAU device.
2011-03-09 15:12:56.679 VDPAU Error: No VDPAU device
2011-03-09 15:12:56.679 VDPAU: Failed to create dummy device.
2011-03-09 15:12:56.680 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-03-09 15:12:56.680 AFD: Opened codec 0x7f9a8442d310, id(MPEG4) type(Video)
2011-03-09 15:12:56.680 AFD: codec AC3 has 2 channels
2011-03-09 15:12:56.681 AFD: Opened codec 0x7f9a8442df30, id(AC3) type(Audio)
2011-03-09 15:12:56.761 AO: Opening audio device 'hdmi:CARD=HDMI,DEV=0' ch 2(2) sr 48000 sf signed 16 bit reenc 1
2011-03-09 15:12:56.810 AudioPlayer: Enabling Audio
2011-03-09 15:12:56.844 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2011-03-09 15:12:56.885 OSD: Base theme size: 1280x720
2011-03-09 15:12:56.885 OSD: Scaling factors: 0.623438x0.622222
2011-03-09 15:12:56.899 OSD: Base theme size: 1280x720
2011-03-09 15:12:56.900 OSD: Scaling factors: 0.623438x0.622222
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 800 x 448
YadifDeint: Using existing thread.
2011-03-09 15:12:56.909 Player(8): Video timing method: USleep with busy wait
2011-03-09 15:12:56.909 TV: Changing from None to WatchingVideo
2011-03-09 15:12:56.970 VideoOutput: Created YV12 OSD.
2011-03-09 15:13:25.707 Player(8): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAUUUUUUUUUuu
2011-03-09 15:13:25.716 Player(8): Waited 100ms for video buffers LAAAAAAAAAAAAAAAAAAAUUUUUUUUUUu
2011-03-09 15:13:28.828 Player(8): Waited 100ms for video buffers UUUUUUUUuuAAAAAAAAAAAAAAAAAAAAU
2011-03-09 15:13:28.837 Player(8): Waited 100ms for video buffers UUUUUUUUUuLAAAAAAAAAAAAAAAAAAAU
2011-03-09 15:13:28.846 Player(8): Waited 100ms for video buffers UUUUUUUUUUuLAAAAAAAAAAAAAAAAAAU
2011-03-09 15:13:29.466 Player(8): Waited 100ms for video buffers AAAAAAAAAAAUUUUUUUUUuuAAAAAAAAA
2011-03-09 15:13:29.475 Player(8): Waited 100ms for video buffers AAAAAAAAAAAUUUUUUUUUuuAAAAAAAAA
2011-03-09 15:13:29.484 Player(8): Waited 100ms for video buffers AAAAAAAAAAAUUUUUUUUUuuAAAAAAAAA
2011-03-09 15:13:29.489 Player(8): Waited 100ms for video buffers AAAAAAAAAAAUUUUUUUUUuuAAAAAAAAA
2011-03-09 15:13:29.594 Player(8): Waited 100ms for video buffers AAAAAAAAAAAUUUUUUUUUuuAAAAAAAAA
2011-03-09 15:13:29.603 Player(8): Waited 100ms for video buffers AAAAAAAAAAAUUUUUUUUUuuAAAAAAAAA
2011-03-09 15:13:29.612 Player(8): Waited 100ms for video buffers AAAAAAAAAAAUUUUUUUUUuuAAAAAAAAA
2011-03-09 15:13:29.617 Player(8): Waited 100ms for video buffers AAAAAAAAAAAUUUUUUUUUuuAAAAAAAAA
2011-03-09 15:13:30.287 Player(8): Waited 100ms for video buffers UuuAAAAAAAAAAAAAAAAAAAAUUUUUUUU
2011-03-09 15:13:30.296 Player(8): Waited 100ms for video buffers UuuAAAAAAAAAAAAAAAAAAAAUUUUUUUU
2011-03-09 15:13:30.305 Player(8): Waited 100ms for video buffers UuuAAAAAAAAAAAAAAAAAAAAUUUUUUUU
2011-03-09 15:13:30.310 Player(8): Waited 100ms for video buffers UuuAAAAAAAAAAAAAAAAAAAAUUUUUUUU
2011-03-09 15:13:30.416 Player(8): Waited 100ms for video buffers UUUuLAAAAAAAAAAAAAAAAAAUUUUUUUU
2011-03-09 15:13:30.920 Player(8): Waited 100ms for video buffers AAUUUUUUUUUuuAAAAAAAAAAAAAAAAAA
2011-03-09 15:13:30.929 Player(8): Waited 100ms for video buffers AAUUUUUUUUUuuAAAAAAAAAAAAAAAAAA
2011-03-09 15:13:30.938 Player(8): Waited 100ms for video buffers AAUUUUUUUUUuuAAAAAAAAAAAAAAAAAA
2011-03-09 15:13:30.943 Player(8): Waited 100ms for video buffers AAUUUUUUUUUuuAAAAAAAAAAAAAAAAAA
2011-03-09 15:13:31.144 Player(8): Waited 100ms for video buffers AAAUUUUUUUUUuuAAAAAAAAAAAAAAAAA
2011-03-09 15:13:31.153 Player(8): Waited 100ms for video buffers AAAUUUUUUUUUuuAAAAAAAAAAAAAAAAA
2011-03-09 15:13:31.162 Player(8): Waited 100ms for video buffers AAAUUUUUUUUUuuAAAAAAAAAAAAAAAAA
2011-03-09 15:13:31.167 Player(8): Waited 100ms for video buffers AAAUUUUUUUUUuuAAAAAAAAAAAAAAAAA
2011-03-09 15:13:31.273 Player(8): Waited 100ms for video buffers AAAUUUUUUUUUuuAAAAAAAAAAAAAAAAA
2011-03-09 15:13:31.282 Player(8): Waited 100ms for video buffers AAAUUUUUUUUUuuAAAAAAAAAAAAAAAAA
2011-03-09 15:13:31.295 Player(8): Waited 100ms for video buffers AAAUUUUUUUUUuuAAAAAAAAAAAAAAAAA
2011-03-09 15:13:33.087 Marking recording as unwatched
2011-03-09 15:13:33.118 TV: Attempting to change from WatchingVideo to None
2011-03-09 15:13:33.640 TV: Changing from WatchingVideo to None

```

---

### Post by williammanda on 2011-03-19
First off I see that you are apparently using the VDPAU selection with a ATI video card...is this correct? If so I would not use that with your card...try another selection that that is less cpu intensive (not VDPAU) along with a lower de-interlacing.
Also please provide your hardware details...with what you have given...it makes it much harder to help.

---

### Post by thatguruguy on 2011-03-19
> **williammanda said:**
> First off I see that you are apparently using the VDPAU selection with a ATI video card...is this correct? If so I would not use that with your card

Bingo. VDPAU doesn't work on ATI cards.

---

### Post by kcaj on 2011-03-19
Motherboard: ASUS M4A785-M
CPU: AMD Athlon II X4 3.0 GHz
Memory: 4 gig
Harddrive: 1 TB
Video: ATI Radeon HD4200 (on motherboard)
Aduio: ATI Radeon HD4200 (on motherboard)
NIC: Realtek RTL8111/8168B gigabit (on motherboard)
Tuners: Silicon Dust HDHomeRun, Hauppauge 950Q USB tuner

Using HDMI (on motherboard) for both Video and Audio.

In Utilities/Setup->Setup->TV Settings->Playback->Playback Profiles [page 3 of 8] I have selected High Quality **not** VDPAU High Quality so I don't know where the VDPAU comes into play, but it always has.

---

### Post by williammanda on 2011-03-19
I have never used ATI...I only use Nvidia but do you have the latest drivers? Please try the next lower playback profile...normal then slim and give your results.

---

### Post by kcaj on 2011-03-19
No change. Here's the log with Normal set:

```
2011-03-19 13:57:47.568 TV: Attempting to change from None to WatchingVideo
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
2011-03-19 13:57:48.547 VDPAU Error: Error at mythrender_vdpau.cpp:1486 (#1, Unknown)
2011-03-19 13:57:48.548 VDPAU Error: Failed to create VDPAU device.
2011-03-19 13:57:48.548 VDPAU Error: No VDPAU device
2011-03-19 13:57:48.548 VDPAU: Failed to create dummy device.
2011-03-19 13:57:48.549 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-03-19 13:57:48.549 AFD: Opened codec 0x7f4908517810, id(MPEG4) type(Video)
2011-03-19 13:57:48.549 AFD: codec AC3 has 6 channels
2011-03-19 13:57:48.550 AFD: Opened codec 0x7f49089ff270, id(AC3) type(Audio)
2011-03-19 13:57:48.679 AO: Opening audio device 'hdmi:CARD=HDMI,DEV=0' ch 2(6) sr 48000 sf signed 16 bit reenc 1
2011-03-19 13:57:48.730 AudioPlayer: Enabling Audio
2011-03-19 13:57:48.779 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2011-03-19 13:57:48.831 OSD: Base theme size: 1280x720
2011-03-19 13:57:48.831 OSD: Scaling factors: 1x0.755556
2011-03-19 13:57:48.873 OSD: Base theme size: 1280x720
2011-03-19 13:57:48.873 OSD: Scaling factors: 1x0.755556
greedyhdeint: size changed from 0 x 0 -> 1280 x 544
2011-03-19 13:57:48.882 Player(0): Video timing method: USleep with busy wait
2011-03-19 13:57:48.882 TV: Changing from None to WatchingVideo
2011-03-19 13:57:48.971 VideoOutput: Created YV12 OSD.
2011-03-19 13:58:03.493 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAUUUUUUUUUuu
2011-03-19 13:58:03.499 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAUUUUUUUUUuu
2011-03-19 13:58:03.515 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAUUUUUUUUUuu
2011-03-19 13:58:05.656 Player(0): Waited 100ms for video buffers AAAAAAUUUUUUUUUUuLAAAAAAAAAAAAA
2011-03-19 13:58:05.662 Player(0): Waited 100ms for video buffers AAAAAAUUUUUUUUUUUUuLAAAAAAAAAAA
2011-03-19 13:58:06.284 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAUUUUUUUUUuuAA
2011-03-19 13:58:06.290 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAUUUUUUUUUuuAA
2011-03-19 13:58:06.307 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAUUUUUUUUUuuAA
2011-03-19 13:58:06.410 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAUUUUUUUUUuuAA
2011-03-19 13:58:06.427 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAUUUUUUUUUuuAA
2011-03-19 13:58:06.433 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAUUUUUUUUUuuAA
2011-03-19 13:58:07.164 Player(0): Waited 100ms for video buffers UUUUUUUUuuAAAAAAAAAAAAAAAAAAAAU
2011-03-19 13:58:07.169 Player(0): Waited 100ms for video buffers UUUUUUUUuuAAAAAAAAAAAAAAAAAAAAU
2011-03-19 13:58:07.186 Player(0): Waited 100ms for video buffers UUUUUUUUuuAAAAAAAAAAAAAAAAAAAAU
2011-03-19 13:58:07.290 Player(0): Waited 100ms for video buffers UUUUUUUUuuAAAAAAAAAAAAAAAAAAAAU
2011-03-19 13:58:07.306 Player(0): Waited 100ms for video buffers UUUUUUUUuuAAAAAAAAAAAAAAAAAAAAU
2011-03-19 13:58:08.086 Player(0): Waited 100ms for video buffers AAAAAAAAAAAUUUUUUUUUuuAAAAAAAAA
2011-03-19 13:58:08.092 Player(0): Waited 100ms for video buffers AAAAAAAAAAAUUUUUUUUUuuAAAAAAAAA
2011-03-19 13:58:08.109 Player(0): Waited 100ms for video buffers AAAAAAAAAAAUUUUUUUUUuuAAAAAAAAA
2011-03-19 13:58:08.212 Player(0): Waited 100ms for video buffers AAAAAAAAAAAUUUUUUUUUuuAAAAAAAAA
2011-03-19 13:58:08.228 Player(0): Waited 100ms for video buffers AAAAAAAAAAAUUUUUUUUUuuAAAAAAAAA
2011-03-19 13:58:08.342 Player(0): Waited 100ms for video buffers AAAAAAAAAAAUUUUUUUUUuuAAAAAAAAA
2011-03-19 13:58:08.348 Player(0): Waited 100ms for video buffers AAAAAAAAAAAUUUUUUUUUuuAAAAAAAAA
2011-03-19 13:58:12.971 Player(0): Waited 100ms for video buffers UUUUuuAAAAAAAAAAAAAAAAAAAAUUUUU
2011-03-19 13:58:12.977 Player(0): Waited 100ms for video buffers UUUUuuAAAAAAAAAAAAAAAAAAAAUUUUU
2011-03-19 13:58:12.993 Player(0): Waited 100ms for video buffers UUUUuuAAAAAAAAAAAAAAAAAAAAUUUUU
2011-03-19 13:58:14.729 Player(0): Waited 100ms for video buffers UUUUUUUUUuuAAAAAAAAAAAAAAAAAAAA
2011-03-19 13:58:14.734 Player(0): Waited 100ms for video buffers UUUUUUUUUuuAAAAAAAAAAAAAAAAAAAA
2011-03-19 13:58:14.751 Player(0): Waited 100ms for video buffers UUUUUUUUUuuAAAAAAAAAAAAAAAAAAAA
2011-03-19 13:58:14.855 Player(0): Waited 100ms for video buffers UUUUUUUUUuuAAAAAAAAAAAAAAAAAAAA
2011-03-19 13:58:14.871 Player(0): Waited 100ms for video buffers UUUUUUUUUuuAAAAAAAAAAAAAAAAAAAA
2011-03-19 13:58:17.637 Player(0): Waited 100ms for video buffers UUUUUUUuuAAAAAAAAAAAAAAAAAAAAUU
2011-03-19 13:58:17.643 Player(0): Waited 100ms for video buffers UUUUUUUuuAAAAAAAAAAAAAAAAAAAAUU
2011-03-19 13:58:17.660 Player(0): Waited 100ms for video buffers UUUUUUUuuAAAAAAAAAAAAAAAAAAAAUU
2011-03-19 13:58:17.763 Player(0): Waited 100ms for video buffers UUUUUUUuuAAAAAAAAAAAAAAAAAAAAUU
2011-03-19 13:58:17.780 Player(0): Waited 100ms for video buffers UUUUUUUuuAAAAAAAAAAAAAAAAAAAAUU
2011-03-19 13:58:17.786 Player(0): Waited 100ms for video buffers UUUUUUUuuAAAAAAAAAAAAAAAAAAAAUU
2011-03-19 13:58:18.442 Player(0): Waited 100ms for video buffers AAAAAAAAAAUUUUUUUUUuuAAAAAAAAAA
2011-03-19 13:58:18.448 Player(0): Waited 100ms for video buffers AAAAAAAAAAUUUUUUUUUuuAAAAAAAAAA
2011-03-19 13:58:18.465 Player(0): Waited 100ms for video buffers AAAAAAAAAAUUUUUUUUUuuAAAAAAAAAA
2011-03-19 13:58:19.595 Player(0): Waited 100ms for video buffers AAAUUUUUUUUUuuAAAAAAAAAAAAAAAAA
2011-03-19 13:58:19.601 Player(0): Waited 100ms for video buffers AAAUUUUUUUUUuuAAAAAAAAAAAAAAAAA
2011-03-19 13:58:19.617 Player(0): Waited 100ms for video buffers AAAUUUUUUUUUuuAAAAAAAAAAAAAAAAA
2011-03-19 13:58:19.698 Marking recording as unwatched
2011-03-19 13:58:19.705 TV: Attempting to change from WatchingVideo to None
2011-03-19 13:58:19.752 TV: Changing from WatchingVideo to None

```And here it is set to Slim:
```
2011-03-19 14:00:32.889 TV: Attempting to change from None to WatchingVideo
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
2011-03-19 14:00:34.037 VDPAU Error: Error at mythrender_vdpau.cpp:1486 (#1, Unknown)
2011-03-19 14:00:34.037 VDPAU Error: Failed to create VDPAU device.
2011-03-19 14:00:34.037 VDPAU Error: No VDPAU device
2011-03-19 14:00:34.037 VDPAU: Failed to create dummy device.
2011-03-19 14:00:34.038 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-03-19 14:00:34.038 AFD: Opened codec 0x7f48f504cf70, id(MPEG4) type(Video)
2011-03-19 14:00:34.038 AFD: codec AC3 has 6 channels
2011-03-19 14:00:34.039 AFD: Opened codec 0x7f48f5038f60, id(AC3) type(Audio)
2011-03-19 14:00:34.156 AO: Opening audio device 'hdmi:CARD=HDMI,DEV=0' ch 2(6) sr 48000 sf signed 16 bit reenc 1
2011-03-19 14:00:34.209 AudioPlayer: Enabling Audio
2011-03-19 14:00:34.247 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2011-03-19 14:00:34.291 OSD: Base theme size: 1280x720
2011-03-19 14:00:34.291 OSD: Scaling factors: 1x0.755556
2011-03-19 14:00:34.309 OSD: Base theme size: 1280x720
2011-03-19 14:00:34.309 OSD: Scaling factors: 1x0.755556
2011-03-19 14:00:34.317 Player(1): Video timing method: USleep with busy wait
2011-03-19 14:00:34.317 TV: Changing from None to WatchingVideo
2011-03-19 14:00:34.453 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAUUUUUUUUuu
2011-03-19 14:00:34.459 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAUUUUUUUUuu
2011-03-19 14:00:34.476 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAUUUUUUUUuu
2011-03-19 14:00:34.580 Player(1): Waited 100ms for video buffers uAAAAAAAAAAAAAAAAAAAAUUUUUUUUUu
2011-03-19 14:00:34.596 Player(1): Waited 100ms for video buffers uAAAAAAAAAAAAAAAAAAAAUUUUUUUUUu
2011-03-19 14:00:34.602 Player(1): Waited 100ms for video buffers uAAAAAAAAAAAAAAAAAAAAUUUUUUUUUu
2011-03-19 14:00:34.706 Player(1): Waited 100ms for video buffers uAAAAAAAAAAAAAAAAAAAAUUUUUUUUUu
2011-03-19 14:00:34.717 Player(1): Waited 100ms for video buffers uAAAAAAAAAAAAAAAAAAAAUUUUUUUUUu
2011-03-19 14:00:34.723 Player(1): Waited 100ms for video buffers uAAAAAAAAAAAAAAAAAAAAUUUUUUUUUu
2011-03-19 14:00:34.837 Player(1): Waited 100ms for video buffers uAAAAAAAAAAAAAAAAAAAAUUUUUUUUUu
2011-03-19 14:00:34.843 Player(1): Waited 100ms for video buffers uAAAAAAAAAAAAAAAAAAAAUUUUUUUUUu
2011-03-19 14:00:34.861 Player(1): Waited 100ms for video buffers uAAAAAAAAAAAAAAAAAAAAUUUUUUUUUu
2011-03-19 14:00:34.964 Player(1): Waited 100ms for video buffers uAAAAAAAAAAAAAAAAAAAAUUUUUUUUUu
2011-03-19 14:00:34.970 Player(1): Waited 100ms for video buffers uAAAAAAAAAAAAAAAAAAAAUUUUUUUUUu
2011-03-19 14:00:34.981 Player(1): Waited 100ms for video buffers uAAAAAAAAAAAAAAAAAAAAUUUUUUUUUu
2011-03-19 14:00:34.987 Player(1): Waited 100ms for video buffers uAAAAAAAAAAAAAAAAAAAAUUUUUUUUUu
2011-03-19 14:00:35.091 Player(1): Waited 100ms for video buffers uAAAAAAAAAAAAAAAAAAAAUUUUUUUUUu
2011-03-19 14:00:35.107 Player(1): Waited 100ms for video buffers uAAAAAAAAAAAAAAAAAAAAUUUUUUUUUu
2011-03-19 14:00:35.227 Player(1): Waited 100ms for video buffers uAAAAAAAAAAAAAAAAAAAAUUUUUUUUUu
2011-03-19 14:00:35.244 Player(1): Waited 100ms for video buffers uAAAAAAAAAAAAAAAAAAAAUUUUUUUUUu
2011-03-19 14:00:35.331 VideoOutput: Created YV12 OSD.
2011-03-19 14:00:37.937 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAUUUUUUUUUuuA
2011-03-19 14:00:37.943 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAUUUUUUUUUuuA
2011-03-19 14:00:37.960 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAUUUUUUUUUuuA
2011-03-19 14:00:38.063 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAUUUUUUUUUuuA
2011-03-19 14:00:38.080 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAUUUUUUUUUuuA
2011-03-19 14:00:38.086 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAUUUUUUUUUuuA
2011-03-19 14:00:38.743 Player(1): Waited 100ms for video buffers UUUUUUUUUuuAAAAAAAAAAAAAAAAAAAA
2011-03-19 14:00:38.748 Player(1): Waited 100ms for video buffers UUUUUUUUUuuAAAAAAAAAAAAAAAAAAAA
2011-03-19 14:00:38.759 Player(1): Waited 100ms for video buffers UUUUUUUUUuuAAAAAAAAAAAAAAAAAAAA
2011-03-19 14:00:38.765 Player(1): Waited 100ms for video buffers UUUUUUUUUuuAAAAAAAAAAAAAAAAAAAA
2011-03-19 14:00:38.869 Player(1): Waited 100ms for video buffers UUUUUUUUUuuAAAAAAAAAAAAAAAAAAAA
2011-03-19 14:00:38.885 Player(1): Waited 100ms for video buffers UUUUUUUUUuuAAAAAAAAAAAAAAAAAAAA
2011-03-19 14:00:40.102 Player(1): Waited 100ms for video buffers UUuuAAAAAAAAAAAAAAAAAAAAUUUUUUU
2011-03-19 14:00:40.108 Player(1): Waited 100ms for video buffers UUuuAAAAAAAAAAAAAAAAAAAAUUUUUUU
2011-03-19 14:00:40.125 Player(1): Waited 100ms for video buffers UUuuAAAAAAAAAAAAAAAAAAAAUUUUUUU
2011-03-19 14:00:40.761 Player(1): Waited 100ms for video buffers AAAAAUUUUUUUUUuuAAAAAAAAAAAAAAA
2011-03-19 14:00:40.767 Player(1): Waited 100ms for video buffers AAAAAUUUUUUUUUuuAAAAAAAAAAAAAAA
2011-03-19 14:00:40.784 Player(1): Waited 100ms for video buffers AAAAAUUUUUUUUUuuAAAAAAAAAAAAAAA
2011-03-19 14:00:41.446 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAUUUUUUUUUuuAAA
2011-03-19 14:00:41.452 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAUUUUUUUUUuuAAA
2011-03-19 14:00:41.468 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAUUUUUUUUUuuAAA
2011-03-19 14:00:42.106 Player(1): Waited 100ms for video buffers UUUUUUUuuAAAAAAAAAAAAAAAAAAAAUU
2011-03-19 14:00:42.123 Player(1): Waited 100ms for video buffers UUUUUUUuuAAAAAAAAAAAAAAAAAAAAUU
2011-03-19 14:00:42.226 Player(1): Waited 100ms for video buffers UUUUUUUuuAAAAAAAAAAAAAAAAAAAAUU
2011-03-19 14:00:42.243 Player(1): Waited 100ms for video buffers UUUUUUUuuAAAAAAAAAAAAAAAAAAAAUU
2011-03-19 14:00:42.363 Player(1): Waited 100ms for video buffers UUUUUUUuuAAAAAAAAAAAAAAAAAAAAUU
2011-03-19 14:00:42.379 Player(1): Waited 100ms for video buffers UUUUUUUuuAAAAAAAAAAAAAAAAAAAAUU
2011-03-19 14:00:43.499 Player(1): Waited 100ms for video buffers uuAAAAAAAAAAAAAAAAAAAAUUUUUUUUU
2011-03-19 14:00:43.505 Player(1): Waited 100ms for video buffers uuAAAAAAAAAAAAAAAAAAAAUUUUUUUUU
2011-03-19 14:00:43.521 Player(1): Waited 100ms for video buffers uuAAAAAAAAAAAAAAAAAAAAUUUUUUUUU
2011-03-19 14:00:43.625 Player(1): Waited 100ms for video buffers uuAAAAAAAAAAAAAAAAAAAAUUUUUUUUU
2011-03-19 14:00:43.642 Player(1): Waited 100ms for video buffers uuAAAAAAAAAAAAAAAAAAAAUUUUUUUUU
2011-03-19 14:00:46.273 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAUUUUUUUUUuu
2011-03-19 14:00:46.279 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAUUUUUUUUUuu
2011-03-19 14:00:46.296 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAUUUUUUUUUuu
2011-03-19 14:00:49.004 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAUUUUUUUUUuuAA
2011-03-19 14:00:49.010 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAUUUUUUUUUuuAA
2011-03-19 14:00:49.027 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAUUUUUUUUUuuAA
2011-03-19 14:00:52.716 Player(1): Waited 100ms for video buffers AAAAAAAAAUUUUUUUUUuuAAAAAAAAAAA
2011-03-19 14:00:52.722 Player(1): Waited 100ms for video buffers AAAAAAAAAUUUUUUUUUuuAAAAAAAAAAA
2011-03-19 14:00:52.739 Player(1): Waited 100ms for video buffers AAAAAAAAAUUUUUUUUUuuAAAAAAAAAAA
2011-03-19 14:00:56.536 Marking recording as unwatched
2011-03-19 14:00:56.575 TV: Attempting to change from WatchingVideo to None
2011-03-19 14:00:56.877 TV: Changing from WatchingVideo to None

```Looking at the manufacturers site my drivers are up to date.
Does this setting govern TV playback, Recorded TV playback *and* Video playback. I cannot see that the setting changes much in video playback but greatly affects Live TV and recorded TV playback.

---

### Post by williammanda on 2011-03-19
First...The VDPAU is puzzling. If your not selecting a VDPAU profile, it shouldn't be using it. The profile effects all the video that is played, some more than others. HD playback is effected more so than videos. So selecting one profile may allow video playback to be good but not HD recorded TV. 
Lastly...I'm not sure what you have invested in this setup, what changes your have made from the original installation but one option is to re-install and see if the VDPAU goes away.

---

### Post by kcaj on 2011-03-21
I'm getting the LP-PPA-mythbuntu-0.24 updates that download ~73 meg once or twice a week. Is that not more or less the equivalent of a reinstall?

---

### Post by williammanda on 2011-03-21
That doesn't affect your settings or something weird going on.

---

### Post by utar on 2011-03-21
I don't know what is happening with vdpau but looking at the log Myth is falling back to XVideo so this is probably not causing your stuttering problem.

Stuttering problems can be caused by the audio sync and other timing issues.  There are a couple of sync related options in Myth, sorry can't remember where and I'm not in front of my box at the moment, but they may be under TV playback.  Have you tried changing these?

I note from your logs that the video that works has MP3 stereo audio and the one that doesn't has AC3 surround sound.  Is this just a coincidence or is this common with all the video that don't work?  If you haven't already I would look at the audio settings section of Myth and perhaps disable sound first to see if that does anything.



Utar

---

### Post by kcaj on 2011-03-21
@williammanda

I thought of that. I queried the settings table for VDPAU: select * from settings where value regexp "vdpau" or data regexp "vdpau'; Nothing came up. But utar is right, VDPAU is rejected when it errors out and the player falls back to XVideo.

@utar

On some of the older tv shows I transcoded using mencoder I used -oac ffmpeg3. The newer ones I'm using -oac copy. But here's the strange thing. I have a couple hundred half hour and hour long tv shows that I transcoded with mencoder and cut the commercials from and they all play fine. They are all using the avi wrapper and some are ac3 and some are mp3. It's only movies that give me the stuttering.  In both cases they are transcoded using mencoder, both are scaled to 720p which in the case of most movies is 1280x544 (2.35:1). But even the movies that are 1280x720 stutter. The only difference is that the tv shows have been edited with avidemux to cut the commercials out. That may be the difference even though avidemux is set to copy audio/video it may be doing something to the output file that mencoder is not... I'll give that a try tonight.

---

### Post by kcaj on 2011-03-22
It appears that avidemux is doing something different than mencoder is in writing the files. I cut the opening production company banners from one movie with avidemux and it played fine. The aggrevating thing is that 0.21 plays all of the files without a flaw...

---

### Post by utar on 2011-03-22
Well at least you are closer to a solution.  I'm a bit surprised that Myth has problems as in my experience the video player on 0.24 is very good and with the exception of the odd HDDVD file plays back everything.

If you haven't already I would try changing the sync / audio options I mentioned in my last post just in case your current setting are causing problems.

Otherwise have you tried muxing to a ts container instead of avi?  In the past I have had issues with different container formats, albeit not with 0.24.  From [http://www.avidemux.org/admWiki/doku.php?id=general:output_formats](http://www.avidemux.org/admWiki/doku.php?id=general:output_formats) I see that avi support for b-frames is not properly supported for example.

[Edit: The forum is messing up the link for some reason.  Just select "output formats" from the menu on the left after following the link.]

---

### Post by kcaj on 2011-03-23
I looked into the audio options. Nothing I did seemed to help. But, I re-encoded a movie using mpeg2 and things are looking good. I didn't have time to watch a whole movie but anything that plays beyond 30 seconds or so is good since the stuttering after 30 seconds became very pronounced.

On the VDPAU thing: The file /usr/lib/libvdpau_nvidia.so is missing from my system, and with good reason, I don't have an Nvidia card. And even if I had the file there would still be an error trying to fire up VDPAU since, again I don't have an nvidia card.

Here's what I do have in the system:
```

[FONT=Courier New]lrwxrwxrwx 1 root root           17 Mar 20 14:03 /usr/lib/libvdpau.so.1 -> libvdpau.so.1.0.0
-rw-r--r-- 1 root root        10480 Jun 26  2010 /usr/lib/libvdpau.so.1.0.0
drwxr-xr-x 2 root root         4096 Oct  7 15:31 /usr/lib/nvidia
-rwxr-xr-x 1 root root          120 Jan 14  2010 /usr/lib/nvidia/pre-install
drwxr-xr-x 2 root root         4096 Oct  7 15:28 /usr/lib/vdpau
lrwxrwxrwx 1 root root           23 Dec 13 19:06 /usr/lib/vdpau/libvdpau_trace.so.1 -> libvdpau_trace.so.1.0.0
-rw-r--r-- 1 root root        51232 Jun 26  2010 /usr/lib/vdpau/libvdpau_trace.so.1.0.0[/FONT]

```Should I leave it as is or try to get the missing files?

---

### Post by pl@yer on 2011-03-23
Why not just export the vidoes folder over nfs, set video folder on the remote frontend at the nfs mount and set the video player to use mplayer. That is what I used to do.

Also don't use vdpau unless using nvidia

---

### Post by utar on 2011-03-23
I think you should have the vdpau file even if you don't have a Nvidia card.  Perhaps Myth didn't upgraded correctly when you starting using autobuilds.  Go just into the package manager and see if that complains about anything.  Otherwise I wouldn't worry about it as your system is working fine.

Glad movies are playing better.  You shouldn't need to reencode the movie through.  You should be able to just remux your recording into a ts container and your software should just recode around cuts if necessary.  The advantages of this is that quality will be better and it will be a lot faster.

I however have never used avidemux so I'm not sure what is supports.

---

### Post by kcaj on 2011-03-23
The videos are stored on a computer in my home office that has around 3 TB of disk space and knows nothing about mytv but exports the videos folder using samba. The folder is then mounted using cifs on two mythtv boxes and as shares on 3 windows boxes. That way I can access the videos from any compter in the house.

The problem I had doing: **mplayer -fs -zoom -quiet %s** is %s got expanded to **myth://Videos@x.x.x.x/FOLDER/FILE** which mplayer did not understand. I wrote a small program to stand between mythtv and mplayer that converted the **myth://Videos@x.x.x.x/** to a more palatable **/mnt/tv/FOLDER/FILE**. and that worked fine although a little klunky. Also using that solution you loose some of the functioality that mythtv provides such as bookmarking.

So now, with the help of a number of people here, I've found that the method I was using to encode the videos appears to be the problem. I've tested one file with a different encoding method and it looks good and I've got a couple more grinding away as we speak to test later on.

I have not told mythtv anywhere in the setup to use vdpau. Mythtv is doing that on it's own. It's not really a problem since the player falls back to xv right away. The only reason I asked about getting the missing files was to elimanate the error message, It would still have to fall back to xv once it discovered that there was no nvidia card present.

---

### Post by pl@yer on 2011-03-24
Ah okay, I get it now. 

I didn't have that problem when I changed the videos path to the local mount point, %s didn't get expanded to anything. I did have mythbackend on the storage machine as well.

---

### Post by nickrout on 2011-03-26
It will only get expanded to a myth:// url if you are using storage groups for mythvideo.

---

### Post by pl@yer on 2011-03-28
> **nickrout said:**
> It will only get expanded to a myth:// url if you are using storage groups for mythvideo.

Okay that must be the difference, thanks

---

