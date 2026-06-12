---
title: "Slow Secondary Backend"
date: 2008-12-17
forum: Mythbuntu
---

### Post by Damanther on 2008-12-17
General Setup:
In my living room I have an older computer( Pentium 4 2G Mhz ) Mythbuntu 8.10 setup running as a secondary backend and frontend with a Hauppage pvr-150 pulling in both NTSC over-the-air broadcasting. It works great.
edit: it has a nvidia 6200 vid card.

I have an pretty hefty AMD x64 machine running my primary mythbackend with a HDHomerun device and a Hauppage HVR1600 pulling in the over-the-air ATSC channels. I run a mythfrontend for this machine in a window. Its my main desktop so I added mythtv to it instead of going with full mythbuntu.
edit: it has an onboard nvidia card. I think its a 7K series.

The only annoyance I have is that if I try to play a recording that was recorded on the primary backend from the frontend in the living room, it pauses every 5 seconds or so. Enough to make it too annoying to watch. I am afraid that this computer is just to slow to play the media streamed from the primary backend but I was hoping you guys here could help me tweak some settings that might help.

Otherwise I LOVE MY MYTHTV SETUP.

---

### Post by ian dobson on 2008-12-17
Hi,

Stuttering could be caused by a slow network connection or a "slow" graphic driver. The Nvidia binary drivers are usually better than the open source ones.

What do you see in the mythfronted.log file? That's usually a good indication of whats wrong.

Regards
Ian Dobson

---

### Post by Damanther on 2008-12-17
Here is the relavant section from my mythfrontend.log

The prebuffering pauses I guess are the delays I'm seeing in the playback.

Any ideas what the "MVs not available" warnin is all about?

I am  using the nvidia driver.

> 
2008-12-17 07:08:21.342 TV: Attempting to change from None to WatchingPreRecorded
2008-12-17 07:08:21.490 DPMS Deactivated
2008-12-17 07:08:22.092 AFD: Opened codec 0x9cde000, id(MPEG2VIDEO) type(Video)
2008-12-17 07:08:22.093 AFD: codec AC3 has 6 channels
2008-12-17 07:08:22.100 AFD: Opened codec 0x9ce7510, id(AC3) type(Audio)
2008-12-17 07:08:22.101 AFD: codec AC3 has 1 channels
2008-12-17 07:08:22.101 AFD: Opened codec 0x98b6d60, id(AC3) type(Audio)
2008-12-17 07:08:22.671 AFD: Opened codec 0x9cdea40, id(MPEG2VIDEO) type(Video)
2008-12-17 07:08:22.671 AFD: codec AC3 has 6 channels
2008-12-17 07:08:22.672 AFD: Opened codec 0xaa6cb80, id(AC3) type(Audio)
2008-12-17 07:08:22.672 AFD: codec AC3 has 1 channels
2008-12-17 07:08:22.673 AFD: Opened codec 0x9cf0bd0, id(AC3) type(Audio)
2008-12-17 07:08:22.682 Opening audio device 'default'. ch 2(2) sr 48000
2008-12-17 07:08:22.682 Opening ALSA audio device 'default'.
2008-12-17 07:08:22.795 mixer unable to find control Master 1
2008-12-17 07:08:23.470 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-12-17 07:08:23.839 OSD Theme Dimensions W: 640 H: 480
2008-12-17 07:08:25.189 TV: Changing from None to WatchingPreRecorded
2008-12-17 07:08:25.191 Realtime priority would require SUID as root.
2008-12-17 07:08:25.305 Video timing method: USleep with busy wait
2008-12-17 07:08:26.302 NVP: prebuffering pause
2008-12-17 07:08:26.482 [mpeg2video @ 0xb7394764]ac-tex damaged at 41 50
2008-12-17 07:08:26.487 [mpeg2video @ 0xb7394764]Warning MVs not available
2008-12-17 07:08:27.374 NVP: prebuffering pause
2008-12-17 07:08:29.304 NVP: prebuffering pause
2008-12-17 07:08:30.746 NVP: prebuffering pause
2008-12-17 07:08:32.051 NVP: prebuffering pause
2008-12-17 07:08:34.073 NVP: prebuffering pause
2008-12-17 07:08:35.528 NVP: prebuffering pause
2008-12-17 07:08:37.648 NVP: prebuffering pause
2008-12-17 07:08:40.840 NVP: prebuffering pause
2008-12-17 07:08:44.032 NVP: prebuffering pause
2008-12-17 07:08:47.006 NVP: prebuffering pause
2008-12-17 07:08:48.492 NVP: prebuffering pause
2008-12-17 07:08:51.436 NVP: prebuffering pause
2008-12-17 07:08:54.606 NVP: prebuffering pause
2008-12-17 07:08:57.225 NVP: prebuffering pause
2008-12-17 07:08:59.941 NVP: prebuffering pause
2008-12-17 07:09:02.994 NVP: prebuffering pause
2008-12-17 07:09:04.995 NVP: prebuffering pause
2008-12-17 07:09:06.209 TV: Attempting to change from WatchingPreRecorded to None


---

### Post by ian dobson on 2008-12-17
Hi,

Try increasing the buffer on the frontend. Could it be that you have a higher bit rate defined for the encoder.

I see "MVs not available" error sometimes from my DVB-c recorders, it doesn't seem to cause any problems and I think you can ignore them.

Regards
Ian Dobson

---

### Post by Damanther on 2008-12-17
OK,

I'm afraid I'm going to have to ask the question.

Which buffer are we talking about, and where to I change it?

Mike

---

### Post by 4dognight on 2008-12-19
You will not be able to playback any HD recordings on your frontend. A P4 2Ghz is not powerful enough. While it is playing back, log in via ssh from the other puter and run top. I will bet the CPU is pegged.

---

