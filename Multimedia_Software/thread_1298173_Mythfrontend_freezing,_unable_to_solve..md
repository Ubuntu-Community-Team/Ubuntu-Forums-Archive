---
title: "Mythfrontend freezing, unable to solve."
date: 2009-10-22
forum: Multimedia Software
---

### Post by Ethan75 on 2009-10-22
Hello,

I'm new to this forum and need help with MythTV. I have MythTV installed on Jaunty 9.04 and everything seems set up correctly and is working well except live TV. At seemingly random intervals Mythfrontend.real freezes, requiring that I either kill the app or stop then restart the service. Immediately preceeding the freeze the audio cuts out then the picture pauses. 

Here is some info on my system:


[LIST]
[*]Ubuntu 9.04
[*]Linux kernal 2.6.28-15-generic
[*]GNOME 2.6.1
[*]AMD Athlon II X2 250 (dual core 3MHz)
[*]2Gb RAM
[*]Gigabyte GA-MA78GM-US2H
[*]Radeon ati 9.9 video driver ('fglrx' is defined in xorg.conf however, per ati-conf)
[*]SG 1Tb HDD (used for media)
[*]SG 320 Gb HDD (used for the OS and installed apps)
[*]TV input source: Motorola DCH3200 connected via firewire
[/LIST]

When the freeze occurs recording on the backend continues as normal. If I exit or restart mythfrontend I can continue watching the recording without hitch. The event does not seem to be timed with any other system event or user input. Here's an excerpt from the frontend log:

2009-10-22 10:44:52.165 TV: Attempting to change from None to WatchingLiveTV
2009-10-22 10:44:52.166 Using protocol version 40
2009-10-22 10:44:54.797 New DB connection, total: 3
2009-10-22 10:44:54.800 Connected to database 'mythconverg' at host: 192.168.1.3
2009-10-22 10:44:54.817 NVP: Disabling Audio, params(-1,2,44100)
2009-10-22 10:44:54.961 DPMS Deactivated 
2009-10-22 10:44:55.018 OSD Theme Dimensions W: 640 H: 480
2009-10-22 10:44:55.354 Realtime priority would require SUID as root.
2009-10-22 10:44:55.355 TV: Changing from None to WatchingLiveTV
2009-10-22 10:44:55.386 Video timing method: USleep with busy wait
2009-10-22 10:44:57.590 AFD: Opened codec 0x4547140, id(MPEG2VIDEO) type(Video)
2009-10-22 10:44:57.590 AFD: codec AC3 has 2 channels
2009-10-22 10:44:57.591 AFD: Opened codec 0x45477c0, id(AC3) type(Audio)
2009-10-22 10:44:57.769 Opening audio device '/dev/adsp'. ch 2(2) sr 48000
2009-10-22 10:44:57.774 Opening OSS audio device '/dev/adsp'.
2009-10-22 10:44:57.782 NVP: Enabling Audio
2009-10-22 10:44:57.790 Opening audio device '/dev/adsp'. ch 2(2) sr 48000
2009-10-22 10:44:57.790 Opening OSS audio device '/dev/adsp'.
2009-10-22 10:45:05.137 [mpeg2video @ 0x7f55114aee70]warning: first frame is no keyframe
2009-10-22 10:45:05.141 [mpeg2video @ 0x7f55114aee70]warning: first frame is no keyframe
2009-10-22 10:45:05.444 NVP: prebuffering pause
2009-10-22 10:45:05.630 [mpeg2video @ 0x7f55114aee70]releasing zombie picture
2009-10-22 10:45:20.943 NVP: prebuffering pause
2009-10-22 10:45:22.576 NVP: prebuffering pause
2009-10-22 10:46:20.104 NVP: Timed out waiting for free video buffers.

Once the timeout has occurred the system freezes and the timeout message repeats until the process is stopped. The timeout message is not always the same, but always seems to be related to prebuffering. The section regarding keyframes is unique to this instance, but typically the 'NVP: prebuffering pause' is preceeded only by the statement 'Opening OSS audio device '/dev/adsp'.' I suspect the root cause is audio based upon the log entries and the fact that I'm using usleep for frame timing, which would explain why the video would crash if there were an audio problem. What I don't get is why this only seems to happen with live tv. Also, CPU usage is only around 10%, and about half of the available memory is consumed at the time of the event.

I've literally spend days trying to diagnose and solve this problem, to no avail. I've spend many hours chasing leads on other forums, each time only to come to a dead end. Hence I'm turning to the community to seek help. 

Thank you in advance for your assistance,

Ethan

---

### Post by Ethan75 on 2009-10-22
I don't want to get too excited yet given all of the false starts I've had, but I may have solved the issue. After setting mythfrontend to open in window mode to keep an eye on CPU and memory performance, I noticed that it crashed once when the update manager started automatically. So I went to start up programs in Preferences and de-selected all programs I didn't need Ubuntu to start at log in. Since then the front end hasn't crashed. 

I don't consider this problem solved yet until I've had at least a few days of stable operation, but it looks promising so far. Hopefully if anyone else is experiencing similar problems this might provide some insight into the cause. I'm still intersted in hearing from others who may have or are currently experiencing this issue. I'd like to understand too if this issue is in fact to due programs attempting to run in the background why mythfrontend is so vulnerable to crashing under these circumstances. 

Any feedback is welcome

---

### Post by Ethan75 on 2009-10-23
Ok, so i've had several more crashes since my last post. I've noticed that the backend is auto-expiring shows moments before the freeze occurs. Not sure if there's a correlation or its simply a coincidence, but nonetheless an observation. I'm very frustrated by the poor stability of MythTV, particularly after all of the effort I've put into it to it already. I'd really appreciate some help with this one.

Ethan

---

### Post by andymcca on 2009-12-15
I am having a similar issue on my chipset 785G based setup. I was thinking it might be driver issues. I have tried the driver from Synaptic as well as the latest .run from ATI. I am not at home right now, so I cannot post logs, but perhaps the following will help:

I noticed slight changes in timing of the freeze (I might get <1s of audio in some cases rather than an immediate freeze) when changing the playback to use ffmpeg. Could be coincidence.

Frontend freezes but Backend continues recording.

Possibly unrelated: Hardware decoding works in VLC, but not in Totem. If Totem is launched to play any hardware decodable video, no output is displayed, and any future attempts to view hardware decoded video in VLC fail (eg Totem breaks video decoding for everyone else).

This install is on a flash drive so I will test live TV playback on another machine tonight to try to isolate driver issues.

---

