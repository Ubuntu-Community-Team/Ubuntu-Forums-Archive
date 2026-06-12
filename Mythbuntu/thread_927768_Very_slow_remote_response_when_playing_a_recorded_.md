---
title: "Very slow remote response when playing a recorded show"
date: 2008-09-23
forum: Mythbuntu
---

### Post by Ransak on 2008-09-23
I recently lost my Tivo to a power failure finally, so I decided to take the plunge with Mythbuntu. I had been saving up hardware for this endeavor for some time, and this is my box:

P4 2.4Ghz Intel CPU
160GB SATA HDD
2 Hauppauge PVR-150 Tuners
nVidia GeForce FX 6200 (AGP) (using DVI)
Packard Bell remote/receiver (with kernel serial disabled per the guide)
Tivo remote
Soundblaster Live! PCI soundcard
1 GB RAM
Onboard Realtek NIC (1GB)
42" Panasonic plasma TV

After a lot of tweaking I have Mythbuntu 8.0.4 (fully patched) installed and working very well. A few minor issues but no major problems, except one.

Most times after a recorded show starts playing the IR remote commands sent to it are 'delayed' by several minutes. If I hit pause for example, it may take as long as ten minutes for it to kick in! It caches all the signals it receives, and once it finally starts to work it then executes them all. Also, once it starts working it appears to work fine for the remainder of the show.

CPU utilization runs pretty high during playback (Xorg probably 80% with mythfrontend taking the remaining 20%), but I checked the lircd process and it's at a faster priority than the mythtv processes. I even reniced it once to a lower priority to see if that would help but it didn't. Playback is smooth even during these periods.

Has anyone else seen this behavior? I'm fairly certain my lirc.conf and lircrc configurations are working since it caches everything and executes it when it finally gets around to paying attention and navigating around the mythtv menus works very well.

Thoughts, ideas, and criticism all welcome!

---

### Post by Ransak on 2008-09-23
Forgot to mention this.

I was digging around in the logs to see if I could find out what was causing this and I found this in dmesg:
```

[  449.181134] lirc_serial: ignoring spike: 1 0 48d7dfd8 48d7dfd8 eef7b ecfc3
[  449.181157] lirc_serial: ignoring spike: 1 0 48d7dfd8 48d7dfd8 eef94 ecfc3
[  970.096527] lirc_serial: ignoring spike: 1 0 48d7e1e2 48d7e1e2 7d420 7d2be
[  970.116131] lirc_serial: ignoring spike: 1 0 48d7e1e2 48d7e1e2 820cb 820c8
[  970.116257] lirc_serial: ignoring spike: 0 0 48d7e1e2 48d7e1e2 8214c 8211b
[  970.851339] lirc_serial: ignoring spike: 1 0 48d7e1e3 48d7e1e3 419e4 413c3
[  970.851507] lirc_serial: ignoring spike: 1 0 48d7e1e3 48d7e1e3 41a8f 41a83
[ 1080.821819] lirc_serial: ignoring spike: 1 0 48d7e251 48d7e251 5a970 588ed
[ 1121.444999] lirc_serial: ignoring spike: 0 0 48d7e27a 48d7e27a a7ba 9e73
[ 1147.775492] lirc_serial: ignoring spike: 1 0 48d7e294 48d7e294 62dfd 62192
[ 1431.951676] lirc_serial: ignoring spike: 0 0 48d7e3b0 48d7e3b0 e128f e0b98
[ 3137.670990] lirc_serial: ignoring spike: 1 0 48d7ea5c 48d7ea5c a82ff a734a
[ 3163.614390] lirc_serial: ignoring spike: 1 0 48d7ea76 48d7ea76 a1f6d a1f69
[ 3359.115128] lirc_serial: ignoring spike: 0 0 48d7eb3a 48d7eb3a 619d1 6118a
[ 3380.291220] lirc_serial: ignoring spike: 1 0 48d7eb4f 48d7eb4f 92da8 92da5
[ 4731.419321] lirc_serial: ignoring spike: 1 0 48d7f098 48d7f098 5c3c6 5b2d4
[ 4731.419338] lirc_serial: ignoring spike: 1 0 48d7f098 48d7f098 5c3dc 5b2d4
[ 4731.419355] lirc_serial: ignoring spike: 1 0 48d7f098 48d7f098 5c3ed 5b2d4
[ 9367.052011] lirc_serial: ignoring spike: 0 0 48d802b9 48d802b9 a5621 a55ab
[ 9367.053377] lirc_serial: ignoring spike: 1 0 48d802b9 48d802b9 a5b7a a5aa7
[ 9367.080734] lirc_serial: ignoring spike: 1 0 48d802b9 48d802b9 ac675 ac5fb
[ 9367.267563] lirc_serial: ignoring spike: 0 0 48d802b9 48d802b9 da126 da11d
[12062.139025] lirc_serial: ignoring spike: 1 0 48d80d44 48d80d44 c266 c1a6
[12062.139338] lirc_serial: ignoring spike: 1 0 48d80d44 48d80d44 c3a2 c396
[12062.180454] lirc_serial: ignoring spike: 0 0 48d80d44 48d80d44 1646e 16122
[12062.187161] lirc_serial: ignoring spike: 0 0 48d80d44 48d80d44 17ea8 1722c
[12062.190364] lirc_serial: ignoring spike: 0 0 48d80d44 48d80d44 18b31 1882c
```

Just for reference, here is my mythfrontend log:

```
dvr@dvr:/var/log/mythtv$ cat mythfrontend.log
SIP: Unknown parameter in -Authenticate; algorithm
SIP Registered to 192.168.1.25 for 3600s
2008-09-23 07:30:03.442 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2008-09-23 07:30:04.933 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:04.933 AFD: codec MP2 has 2 channels
2008-09-23 07:30:04.933 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:30:13.156 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:13.156 AFD: codec MP2 has 2 channels
2008-09-23 07:30:13.156 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:30:14.964 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:14.964 AFD: codec MP2 has 2 channels
2008-09-23 07:30:14.965 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:30:26.254 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:26.254 AFD: codec MP2 has 2 channels
2008-09-23 07:30:26.254 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:30:28.664 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:28.664 AFD: codec MP2 has 2 channels
2008-09-23 07:30:28.665 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:30:32.605 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:32.605 AFD: codec MP2 has 2 channels
2008-09-23 07:30:32.606 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:30:34.356 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:34.356 AFD: codec MP2 has 2 channels
2008-09-23 07:30:34.356 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:30:36.029 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:36.029 AFD: codec MP2 has 2 channels
2008-09-23 07:30:36.029 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:30:36.578 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:36.579 AFD: codec MP2 has 2 channels
2008-09-23 07:30:36.579 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:30:40.523 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:40.523 AFD: codec MP2 has 2 channels
2008-09-23 07:30:40.523 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:30:42.857 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:42.857 AFD: codec MP2 has 2 channels
2008-09-23 07:30:42.857 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:30:43.745 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:43.745 AFD: codec MP2 has 2 channels
2008-09-23 07:30:43.745 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:30:45.812 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:45.812 AFD: codec MP2 has 2 channels
2008-09-23 07:30:45.813 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:30:47.965 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:47.965 AFD: codec MP2 has 2 channels
2008-09-23 07:30:47.966 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:30:51.576 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:51.576 AFD: codec MP2 has 2 channels
2008-09-23 07:30:51.577 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:30:52.434 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:52.434 AFD: codec MP2 has 2 channels
2008-09-23 07:30:52.435 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:30:53.445 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:53.445 AFD: codec MP2 has 2 channels
2008-09-23 07:30:53.445 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:30:59.469 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:30:59.469 AFD: codec MP2 has 2 channels
2008-09-23 07:30:59.469 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:31:00.647 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:31:00.647 AFD: codec MP2 has 2 channels
2008-09-23 07:31:00.648 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:31:23.596 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:31:23.596 AFD: codec MP2 has 2 channels
2008-09-23 07:31:23.596 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:31:27.221 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:31:27.221 AFD: codec MP2 has 2 channels
2008-09-23 07:31:27.221 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:31:32.599 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:31:32.599 AFD: codec MP2 has 2 channels
2008-09-23 07:31:32.599 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:31:33.570 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:31:33.571 AFD: codec MP2 has 2 channels
2008-09-23 07:31:33.571 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:31:34.460 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:31:34.460 AFD: codec MP2 has 2 channels
2008-09-23 07:31:34.460 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:31:35.309 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:31:35.309 AFD: codec MP2 has 2 channels
2008-09-23 07:31:35.309 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:31:36.737 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:31:36.737 AFD: codec MP2 has 2 channels
2008-09-23 07:31:36.737 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:31:37.091 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:31:37.091 AFD: codec MP2 has 2 channels
2008-09-23 07:31:37.091 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:31:37.521 [mpeg2video @ 0xb73a5a88]invalid cbp at 37 19
2008-09-23 07:31:37.521 [mpeg2video @ 0xb73a5a88]Warning MVs not available
2008-09-23 07:31:37.561 TV: Attempting to change from None to WatchingPreRecorded
2008-09-23 07:31:37.580 DPMS Deactivated 
2008-09-23 07:31:37.782 AFD: Opened codec 0x908bb10, id(MPEG2VIDEO) type(Video)
2008-09-23 07:31:37.782 AFD: codec MP2 has 2 channels
2008-09-23 07:31:37.782 AFD: Opened codec 0x8327a80, id(MP2) type(Audio)
2008-09-23 07:31:37.787 Opening audio device 'default'. ch 2(2) sr 48000
2008-09-23 07:31:37.787 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-09-23 07:31:37.790 AudioOutput Warning: Mixer attach error -2: No such file or directory
                        Check Mixer Name in Setup: '/dev/mixer'
2008-09-23 07:31:37.939 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-09-23 07:31:38.012 OSD Theme Dimensions W: 640 H: 480
2008-09-23 07:31:38.750 TV: Changing from None to WatchingPreRecorded
2008-09-23 07:31:38.754 Realtime priority would require SUID as root.
2008-09-23 07:31:38.852 Video timing method: USleep with busy wait
2008-09-23 07:32:06.962 WriteAudio: buffer underrun
2008-09-23 07:40:05.372 DPMS Reactivated.
2008-09-23 07:40:05.399 DPMS Deactivated 
2008-09-23 07:40:19.520 DPMS Reactivated.
2008-09-23 07:40:19.609 DPMS Deactivated 
2008-09-23 07:40:21.786 DPMS Reactivated.
2008-09-23 07:41:58.788 DPMS Deactivated 
2008-09-23 07:43:49.263 TV: Attempting to change from WatchingPreRecorded to None
2008-09-23 07:43:49.398 TV: Changing from WatchingPreRecorded to None
2008-09-23 07:43:49.489 DPMS Reactivated.
2008-09-23 07:43:49.674 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 07:43:49.674 AFD: codec MP2 has 2 channels
2008-09-23 07:43:49.674 AFD: Opened codec 0x8aa4010, id(MP2) type(Audio)
2008-09-23 07:43:50.214 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 07:43:50.215 AFD: codec MP2 has 2 channels
2008-09-23 07:43:50.215 AFD: Opened codec 0x8aa4010, id(MP2) type(Audio)
2008-09-23 07:43:50.635 [mpeg2video @ 0xb73a5a88]invalid cbp at 37 19
2008-09-23 07:43:50.635 [mpeg2video @ 0xb73a5a88]Warning MVs not available
2008-09-23 07:43:51.270 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 07:43:51.271 AFD: codec MP2 has 2 channels
2008-09-23 07:43:51.271 AFD: Opened codec 0x8aa4010, id(MP2) type(Audio)
2008-09-23 07:58:49.245 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 07:58:49.245 AFD: codec MP2 has 2 channels
2008-09-23 07:58:49.245 AFD: Opened codec 0x8aa4010, id(MP2) type(Audio)
2008-09-23 08:11:03.051 [mpeg2video @ 0xb73a5a88]ac-tex damaged at 39 28
2008-09-23 08:11:03.051 [mpeg2video @ 0xb73a5a88]Warning MVs not available
2008-09-23 08:11:03.717 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 08:11:03.717 AFD: codec MP2 has 2 channels
2008-09-23 08:11:03.717 AFD: Opened codec 0x8a2d8b0, id(MP2) type(Audio)
2008-09-23 08:11:21.658 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 08:11:21.658 AFD: codec MP2 has 2 channels
2008-09-23 08:11:21.658 AFD: Opened codec 0x8a2d8b0, id(MP2) type(Audio)
2008-09-23 08:11:29.361 TV: Attempting to change from None to WatchingPreRecorded
2008-09-23 08:11:29.376 DPMS Deactivated 
2008-09-23 08:11:29.581 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 08:11:29.582 AFD: codec MP2 has 2 channels
2008-09-23 08:11:29.582 AFD: Opened codec 0x8a2d8b0, id(MP2) type(Audio)
2008-09-23 08:11:29.586 Opening audio device 'default'. ch 2(2) sr 48000
2008-09-23 08:11:29.586 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-09-23 08:11:29.589 AudioOutput Warning: Mixer attach error -2: No such file or directory
                        Check Mixer Name in Setup: '/dev/mixer'
2008-09-23 08:11:29.705 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-09-23 08:11:29.774 OSD Theme Dimensions W: 640 H: 480
2008-09-23 08:11:30.497 TV: Changing from None to WatchingPreRecorded
2008-09-23 08:11:30.500 Realtime priority would require SUID as root.
2008-09-23 08:11:30.600 Video timing method: USleep with busy wait
2008-09-23 08:20:28.198 DPMS Reactivated.
2008-09-23 08:20:34.679 DPMS Deactivated 
2008-09-23 08:22:40.146 WriteAudio: buffer underrun
2008-09-23 08:23:29.373 WriteAudio: buffer underrun
2008-09-23 08:23:29.602 DPMS Reactivated.
2008-09-23 08:23:29.716 TV: Attempting to change from WatchingPreRecorded to None
2008-09-23 08:23:29.845 TV: Changing from WatchingPreRecorded to None
2008-09-23 08:23:30.101 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 08:23:30.101 AFD: codec MP2 has 2 channels
2008-09-23 08:23:30.101 AFD: Opened codec 0x8a2d8b0, id(MP2) type(Audio)
2008-09-23 08:23:30.682 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 08:23:30.682 AFD: codec MP2 has 2 channels
2008-09-23 08:23:30.682 AFD: Opened codec 0x8a2d8b0, id(MP2) type(Audio)
2008-09-23 08:23:31.746 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 08:23:31.746 AFD: codec MP2 has 2 channels
2008-09-23 08:23:31.746 AFD: Opened codec 0x8a2d8b0, id(MP2) type(Audio)
2008-09-23 08:23:36.369 [mpeg2video @ 0xb73a5a88]invalid cbp at 39 20
2008-09-23 08:23:36.369 [mpeg2video @ 0xb73a5a88]Warning MVs not available
2008-09-23 08:23:36.408 TV: Attempting to change from None to WatchingPreRecorded
2008-09-23 08:23:36.428 DPMS Deactivated 
2008-09-23 08:23:36.628 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 08:23:36.628 AFD: codec MP2 has 2 channels
2008-09-23 08:23:36.628 AFD: Opened codec 0x8a2d8b0, id(MP2) type(Audio)
2008-09-23 08:23:36.633 Opening audio device 'default'. ch 2(2) sr 48000
2008-09-23 08:23:36.633 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-09-23 08:23:36.636 AudioOutput Warning: Mixer attach error -2: No such file or directory
                        Check Mixer Name in Setup: '/dev/mixer'
2008-09-23 08:23:36.719 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-09-23 08:23:36.790 OSD Theme Dimensions W: 640 H: 480
2008-09-23 08:23:37.460 TV: Changing from None to WatchingPreRecorded
2008-09-23 08:23:37.464 Realtime priority would require SUID as root.
2008-09-23 08:23:37.564 Video timing method: USleep with busy wait
2008-09-23 08:23:38.774 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-23 08:23:38.774 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-23 08:23:40.492 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-23 08:23:40.492 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-23 08:23:40.493 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-23 08:23:40.494 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-23 08:23:40.497 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-23 08:23:40.499 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-23 08:24:00.398 WriteAudio: buffer underrun
2008-09-23 08:24:58.361 DPMS Reactivated.
2008-09-23 08:25:05.329 TV: Attempting to change from WatchingPreRecorded to None
2008-09-23 08:25:05.426 TV: Changing from WatchingPreRecorded to None
2008-09-23 08:25:05.775 TV: Attempting to change from None to WatchingPreRecorded
2008-09-23 08:25:05.805 New DB connection, total: 3
2008-09-23 08:25:05.805 Connected to database 'mythconverg' at host: localhost
2008-09-23 08:25:05.809 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 08:25:05.810 AFD: codec MP2 has 2 channels
2008-09-23 08:25:05.810 AFD: Opened codec 0x8ac1e20, id(MP2) type(Audio)
2008-09-23 08:25:05.846 DPMS Deactivated 
2008-09-23 08:25:06.056 AFD: Opened codec 0x8a2d8b0, id(MPEG2VIDEO) type(Video)
2008-09-23 08:25:06.056 AFD: codec MP2 has 2 channels
2008-09-23 08:25:06.056 AFD: Opened codec 0x8aad3d0, id(MP2) type(Audio)
2008-09-23 08:25:06.058 Opening audio device 'default'. ch 2(2) sr 48000
2008-09-23 08:25:06.058 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-09-23 08:25:06.061 AudioOutput Warning: Mixer attach error -2: No such file or directory
                        Check Mixer Name in Setup: '/dev/mixer'
2008-09-23 08:25:06.146 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-09-23 08:25:06.196 OSD Theme Dimensions W: 640 H: 480
2008-09-23 08:25:06.792 TV: Changing from None to WatchingPreRecorded
2008-09-23 08:25:06.795 Realtime priority would require SUID as root.
2008-09-23 08:25:06.892 Video timing method: USleep with busy wait
2008-09-23 08:25:09.004 TV: Attempting to change from WatchingPreRecorded to None
2008-09-23 08:25:09.108 TV: Changing from WatchingPreRecorded to None
2008-09-23 08:25:09.278 DPMS Reactivated.
2008-09-23 08:25:09.856 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 08:25:09.856 AFD: codec MP2 has 2 channels
2008-09-23 08:25:09.856 AFD: Opened codec 0x8a2d8b0, id(MP2) type(Audio)
2008-09-23 08:25:10.192 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 08:25:10.192 AFD: codec MP2 has 2 channels
2008-09-23 08:25:10.192 AFD: Opened codec 0x8a2d8b0, id(MP2) type(Audio)
2008-09-23 08:25:10.918 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 08:25:10.918 AFD: codec MP2 has 2 channels
2008-09-23 08:25:10.919 AFD: Opened codec 0x8a2d8b0, id(MP2) type(Audio)
2008-09-23 08:25:14.080 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 08:25:14.081 AFD: codec MP2 has 2 channels
2008-09-23 08:25:14.081 AFD: Opened codec 0x8a2d8b0, id(MP2) type(Audio)
2008-09-23 08:25:40.077 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 08:25:40.078 AFD: codec MP2 has 2 channels
2008-09-23 08:25:40.078 AFD: Opened codec 0x8a2d8b0, id(MP2) type(Audio)
2008-09-23 08:25:43.000 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 08:25:43.000 AFD: codec MP2 has 2 channels
2008-09-23 08:25:43.001 AFD: Opened codec 0x8a2d8b0, id(MP2) type(Audio)
2008-09-23 08:25:46.716 AFD: Opened codec 0x8327a80, id(MPEG2VIDEO) type(Video)
2008-09-23 08:25:46.716 AFD: codec MP2 has 2 channels
2008-09-23 08:25:46.716 AFD: Opened codec 0x8a2d8b0, id(MP2) type(Audio)
2008-09-23 08:25:53.450 [mpeg2video @ 0xb73a5a88]ac-tex damaged at 35 28
2008-09-23 08:25:53.450 [mpeg2video @ 0xb73a5a88]Warning MVs not available
SIP: Unknown parameter in -Authenticate; algorithm
SIP Registered to 192.168.1.25 for 3600s
SIP: Unknown parameter in -Authenticate; algorithm
SIP Registered to 192.168.1.25 for 3600s
2008-09-23 10:04:35.266 No theme dir: /home/dvr/.mythtv/themes/Mythbuntu-8.04
2008-09-23 10:04:44.567 No theme dir: /home/dvr/.mythtv/themes/Mythbuntu-8.04
2008-09-23 10:04:46.824 No theme dir: /home/dvr/.mythtv/themes/Mythbuntu-8.04
2008-09-23 10:04:55.538 No theme dir: /home/dvr/.mythtv/themes/Mythbuntu-8.04
2008-09-23 10:05:08.005 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2008-09-23 10:05:09.366 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:09.366 AFD: codec MP2 has 2 channels
2008-09-23 10:05:09.367 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:12.401 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:12.401 AFD: codec MP2 has 2 channels
2008-09-23 10:05:12.402 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:13.309 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:13.309 AFD: codec MP2 has 2 channels
2008-09-23 10:05:13.309 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:14.093 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:14.093 AFD: codec MP2 has 2 channels
2008-09-23 10:05:14.093 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:16.080 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:16.080 AFD: codec MP2 has 2 channels
2008-09-23 10:05:16.081 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:17.543 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:17.543 AFD: codec MP2 has 2 channels
2008-09-23 10:05:17.543 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:20.673 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:20.673 AFD: codec MP2 has 2 channels
2008-09-23 10:05:20.673 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:21.093 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:21.093 AFD: codec MP2 has 2 channels
2008-09-23 10:05:21.093 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:21.772 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:21.772 AFD: codec MP2 has 2 channels
2008-09-23 10:05:21.773 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:22.502 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:22.502 AFD: codec MP2 has 2 channels
2008-09-23 10:05:22.502 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:23.376 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:23.376 AFD: codec MP2 has 2 channels
2008-09-23 10:05:23.376 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:24.354 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:24.354 AFD: codec MP2 has 2 channels
2008-09-23 10:05:24.354 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:24.904 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:24.904 AFD: codec MP2 has 2 channels
2008-09-23 10:05:24.904 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:26.689 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:26.689 AFD: codec MP2 has 2 channels
2008-09-23 10:05:26.689 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:29.221 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:29.221 AFD: codec MP2 has 2 channels
2008-09-23 10:05:29.221 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:29.847 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:29.847 AFD: codec MP2 has 2 channels
2008-09-23 10:05:29.847 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:30.371 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:30.371 AFD: codec MP2 has 2 channels
2008-09-23 10:05:30.371 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:31.147 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:31.148 AFD: codec MP2 has 2 channels
2008-09-23 10:05:31.148 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:31.898 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:31.898 AFD: codec MP2 has 2 channels
2008-09-23 10:05:31.899 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:42.013 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:42.013 AFD: codec MP2 has 2 channels
2008-09-23 10:05:42.013 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:46.104 AFD: Opened codec 0x84acff0, id(MPEG2VIDEO) type(Video)
2008-09-23 10:05:46.104 AFD: codec MP2 has 2 channels
2008-09-23 10:05:46.104 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:05:49.640 [mpeg2video @ 0xb73a5a88]ac-tex damaged at 29 10
2008-09-23 10:05:49.640 [mpeg2video @ 0xb73a5a88]Warning MVs not available
2008-09-23 10:05:57.513 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2008-09-23 10:06:24.273 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2008-09-23 10:06:30.125 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/keyboard/en_us_ui.xml
2008-09-23 10:08:28.721 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2008-09-23 10:08:44.272 No theme dir: /home/dvr/.mythtv/themes/Mythbuntu-8.04
2008-09-23 10:08:45.108 TV: Attempting to change from None to WatchingLiveTV
2008-09-23 10:08:45.109 Using protocol version 40
2008-09-23 10:08:47.221 DPMS Deactivated 
2008-09-23 10:08:48.045 AFD: Opened codec 0x84c9e80, id(MPEG2VIDEO) type(Video)
2008-09-23 10:08:48.045 AFD: codec MP2 has 2 channels
2008-09-23 10:08:48.045 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:08:48.098 Opening audio device 'default'. ch 2(2) sr 48000
2008-09-23 10:08:48.098 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-09-23 10:08:48.104 AudioOutput Warning: Mixer attach error -2: No such file or directory
                        Check Mixer Name in Setup: '/dev/mixer'
2008-09-23 10:08:48.177 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-09-23 10:08:48.237 OSD Theme Dimensions W: 640 H: 480
2008-09-23 10:08:48.863 TV: Changing from None to WatchingLiveTV
2008-09-23 10:08:48.876 Realtime priority would require SUID as root.
2008-09-23 10:08:48.972 Video timing method: USleep with busy wait
2008-09-23 10:08:52.162 TV: Attempting to change from WatchingLiveTV to None
2008-09-23 10:08:52.407 TV: Changing from WatchingLiveTV to None
2008-09-23 10:08:52.425 DPMS Reactivated.
2008-09-23 10:09:07.172 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2008-09-23 10:09:08.482 AFD: Opened codec 0x9324630, id(MPEG2VIDEO) type(Video)
2008-09-23 10:09:08.482 AFD: codec MP2 has 2 channels
2008-09-23 10:09:08.482 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:09:22.548 AFD: Opened codec 0x84d5440, id(MPEG2VIDEO) type(Video)
2008-09-23 10:09:22.548 AFD: codec MP2 has 2 channels
2008-09-23 10:09:22.548 AFD: Opened codec 0x9324630, id(MP2) type(Audio)
2008-09-23 10:09:24.790 AFD: Opened codec 0x9324630, id(MPEG2VIDEO) type(Video)
2008-09-23 10:09:24.791 AFD: codec MP2 has 2 channels
2008-09-23 10:09:24.791 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:09:25.896 AFD: Opened codec 0x84d5440, id(MPEG2VIDEO) type(Video)
2008-09-23 10:09:25.896 AFD: codec MP2 has 2 channels
2008-09-23 10:09:25.896 AFD: Opened codec 0x9324630, id(MP2) type(Audio)
2008-09-23 10:09:27.371 AFD: Opened codec 0x9324630, id(MPEG2VIDEO) type(Video)
2008-09-23 10:09:27.371 AFD: codec MP2 has 2 channels
2008-09-23 10:09:27.372 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:09:28.470 AFD: Opened codec 0x84d5440, id(MPEG2VIDEO) type(Video)
2008-09-23 10:09:28.471 AFD: codec MP2 has 2 channels
2008-09-23 10:09:28.471 AFD: Opened codec 0x9324630, id(MP2) type(Audio)
2008-09-23 10:09:29.779 AFD: Opened codec 0x9324630, id(MPEG2VIDEO) type(Video)
2008-09-23 10:09:29.779 AFD: codec MP2 has 2 channels
2008-09-23 10:09:29.779 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:09:31.901 AFD: Opened codec 0x84d5440, id(MPEG2VIDEO) type(Video)
2008-09-23 10:09:31.901 AFD: codec MP2 has 2 channels
2008-09-23 10:09:31.901 AFD: Opened codec 0x9324630, id(MP2) type(Audio)
2008-09-23 10:09:32.519 AFD: Opened codec 0x9324630, id(MPEG2VIDEO) type(Video)
2008-09-23 10:09:32.519 AFD: codec MP2 has 2 channels
2008-09-23 10:09:32.519 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:09:34.721 AFD: Opened codec 0x84d5440, id(MPEG2VIDEO) type(Video)
2008-09-23 10:09:34.721 AFD: codec MP2 has 2 channels
2008-09-23 10:09:34.721 AFD: Opened codec 0x9324630, id(MP2) type(Audio)
2008-09-23 10:09:35.062 AFD: Opened codec 0x9324630, id(MPEG2VIDEO) type(Video)
2008-09-23 10:09:35.062 AFD: codec MP2 has 2 channels
2008-09-23 10:09:35.062 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:09:37.281 AFD: Opened codec 0x84d5440, id(MPEG2VIDEO) type(Video)
2008-09-23 10:09:37.281 AFD: codec MP2 has 2 channels
2008-09-23 10:09:37.281 AFD: Opened codec 0x9324630, id(MP2) type(Audio)
2008-09-23 10:09:37.992 AFD: Opened codec 0x9324630, id(MPEG2VIDEO) type(Video)
2008-09-23 10:09:37.992 AFD: codec MP2 has 2 channels
2008-09-23 10:09:37.992 AFD: Opened codec 0x84d5440, id(MP2) type(Audio)
2008-09-23 10:09:38.696 TV: Attempting to change from None to WatchingPreRecorded
2008-09-23 10:09:38.712 DPMS Deactivated 
2008-09-23 10:09:38.910 AFD: Opened codec 0x84d5440, id(MPEG2VIDEO) type(Video)
2008-09-23 10:09:38.910 AFD: codec MP2 has 2 channels
2008-09-23 10:09:38.910 AFD: Opened codec 0x9324630, id(MP2) type(Audio)
2008-09-23 10:09:38.915 Opening audio device 'default'. ch 2(2) sr 48000
2008-09-23 10:09:38.915 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-09-23 10:09:38.918 AudioOutput Warning: Mixer attach error -2: No such file or directory
                        Check Mixer Name in Setup: '/dev/mixer'
2008-09-23 10:09:39.281 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-09-23 10:09:39.334 OSD Theme Dimensions W: 640 H: 480
2008-09-23 10:09:39.937 TV: Changing from None to WatchingPreRecorded
2008-09-23 10:09:39.941 Realtime priority would require SUID as root.
2008-09-23 10:09:40.040 Video timing method: USleep with busy wait
2008-09-23 10:20:29.693 DPMS Reactivated.
SIP: Unknown parameter in -Authenticate; algorithm
SIP Registered to 192.168.1.25 for 3600s
2008-09-23 10:30:30.078 DPMS Deactivated 
2008-09-23 10:30:30.078 DPMS Reactivated.
2008-09-23 10:30:30.081 DPMS Deactivated 
2008-09-23 10:30:30.858 DPMS Reactivated.
2008-09-23 10:30:31.170 DPMS Deactivated 
2008-09-23 10:30:32.538 WriteAudio: buffer underrun
2008-09-23 10:30:32.584 DPMS Reactivated.
2008-09-23 10:30:32.937 DPMS Deactivated 
2008-09-23 10:31:27.188 DPMS Reactivated.
```

---

### Post by Ransak on 2008-09-23
Well, I found this:

[http://www.nabble.com/lirc_gpio-tt15254916.html#a15299722](http://www.nabble.com/lirc_gpio-tt15254916.html#a15299722)

And this:

[http://www.mythtv.org/pipermail/mythtv-users/2008-March/214267.html](http://www.mythtv.org/pipermail/mythtv-users/2008-March/214267.html)

... and this:

[http://mysettopbox.tv/phpBB2/viewtopic.php?p=114702&sid=1584aa8ed79a31004fce47d8a0e26ddc](http://mysettopbox.tv/phpBB2/viewtopic.php?p=114702&sid=1584aa8ed79a31004fce47d8a0e26ddc)

It appears to be the same issue (I think). It appears that there's an interrupt issue causing the delays, possibly the capture card driver requesting the interrupt to be disabled too long. I'll post more if I find anything else out.

---

### Post by Ransak on 2008-09-23
Information from dmesg on this serial port:


```
[   27.714638] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.714769] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.715751] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```

dmesg info on lirc:

```
[   75.073876] lirc_dev: IR Remote Control driver registered, at major 61 
[   75.584928] lirc_serial: auto-detected active high receiver
[   75.584937] lirc_dev: lirc_register_plugin: sample_rate: 0
```

And cat /proc/interrupts:

```
dvr@dvr:~$ cat /proc/interrupts
           CPU0       
  0:        308   IO-APIC-edge      timer
  1:          2   IO-APIC-edge      i8042
  4:          2   IO-APIC-edge      lirc_serial
  5:          0   IO-APIC-edge      MPU401 UART
  6:          5   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          3   IO-APIC-edge      rtc
  9:          0   IO-APIC-fasteoi   acpi
 12:          4   IO-APIC-edge      i8042
 14:       2624   IO-APIC-edge      libata
 15:          0   IO-APIC-edge      libata
 16:        663   IO-APIC-fasteoi   ivtv1, eth0
 17:        212   IO-APIC-fasteoi   ohci_hcd:usb1
 18:          0   IO-APIC-fasteoi   ohci_hcd:usb2
 19:          0   IO-APIC-fasteoi   ohci_hcd:usb3
 20:      19231   IO-APIC-fasteoi   EMU10K1, nvidia
 21:          2   IO-APIC-fasteoi   ehci_hcd:usb4
 22:      10620   IO-APIC-fasteoi   sata_sis
 23:          0   IO-APIC-fasteoi   ivtv0
NMI:          0   Non-maskable interrupts
LOC:      76705   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0

```

---

### Post by bmathis on 2008-09-23
I experienced the same issue last night after building a new myth box using an Athlon 64.

---

### Post by newlinux on 2008-09-23
another perspective, in case your problem is like mine. Have you tested if your keyboard has the same problem, or whether or not this happens using the internal player in mythvideo? Just in case your problem is like mine and others...

[http://ubuntuforums.org/showthread.php?p=5821867](http://ubuntuforums.org/showthread.php?p=5821867)

[http://ubuntuforums.org/showthread.php?p=5816936](http://ubuntuforums.org/showthread.php?p=5816936)

---

### Post by Ransak on 2008-09-23
Thanks for the links! I made the same change to xorg.conf that was listed in those posts. I'm not at home at the moment so I fired up a recorded video over VNC and the CPU utilization appears to be **much** lower (now around 20% for mythfrontend and 2% for Xorg). I'll test the remote tonight to see how it works.

---

### Post by bmathis on 2008-09-23
thanks newlinux, adding this option to my xorg file under devices seemed to have worked for me.

```
Option "UseEvents" "on"
```

---

### Post by Ransak on 2008-09-24
It helped me as well. Thanks!

---

### Post by sgtstadanko on 2008-11-05
could share your tivo remote configs and your lircrc?  i have a streamzap ir receiver and cant get it working.  the receiver lights up so i know its getting signal.

---

### Post by Ransak on 2008-11-13
Sure sgtstadanko. I'm assuming you want the file .lircrc references for mythtv:

```

# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu
begin
    remote = PackBell
    prog = mythtv
    button = Seven
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = One
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Down
    config = Down
    repeat = 2
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Zero
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Six
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Two
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = CHDown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = CHUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = VolDown
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = VolUp
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Five
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Display
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Four
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Enter
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Up
    config = Up
    repeat = 2
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Nine
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Three
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Enter
    config = Enter
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Eight
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = SRS
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = PackBell
    prog = mythtv
    button = Aux3
    config = p
    repeat = 0
    delay = 0
end

begin
prog = mythtv
button = 1_ENTER/LAST
repeat = 0
delay = 0
config = H
end

#begin
#prog = mythtv 
#button = 1_TV_POWER
#repeat = 3
#config = Esc,Esc
#end

# begin
# prog = mythtv
# button = TVINPUT
# repeat = 3
# config = F
# end

begin
prog = mythtv
button = 1_CH/PAGE_UP
repeat = 0
delay = 0
config = Up
end

begin
prog = mythtv
button = 1_CH/PAGE_DOWN
repeat = 0
delay = 0
config = Down
end

begin
prog = mythtv
button = 1_TH_UP
repeat = 0
delay = 0
config = PgDown
end

begin
prog = mythtv
button = 1_TH_DOWN
repeat = 0
delay = 0
config = PgUp
end

begin
prog = mythtv
button = 1_TIVO
repeat = 0
delay = 0
config = Esc
end

begin
prog = mythtv
button = 1_WINDOW
repeat = 0
delay = 0
config = F2
end

begin
prog = mythtv
button = 1_LIVE_TV
repeat = 0
delay = 0
config = F1
end

begin
prog = mythtv
button = 1_RECORD
repeat = 0
delay = 0
config = R
end

begin
prog = mythtv
button = 1_CLEAR
repeat = 0
delay = 0
config = D
end

begin
prog = mythtv
button = 1_GUIDE
repeat = 0
delay = 0
config = M
end

begin
prog = mythtv
button = 1_INFO
repeat = 0
delay = 0
config = I
end

begin
prog = mythtv
button = 1_UP
repeat = 1
delay = 3
config = Up
end

begin
prog = mythtv
button = 1_RIGHT
repeat = 0
delay = 0
config = Right
end

begin
prog = mythtv
button = 1_FORWARD
repeat = 0
delay = 0
config = >,>,>
end

begin
prog = mythtv
button = 1_DOWN
repeat = 1
delay = 3
config = Down
end

begin
prog = mythtv
button = 1_LEFT
repeat = 0
delay = 0
config = Left
end

begin
prog = mythtv
button = 1_REWIND
repeat = 0
config = <,<,<
end

begin
prog = mythtv
button = 1_PLAY
repeat = 0
config = Return
end

begin
prog = mythtv
button = 1_PAUSE
repeat = 0
config = P
end

begin
prog = mythtv
button = 1_SLOW
repeat = 0
config = F3
end

begin
prog = mythtv
button = 1_JUMP
repeat = 0
config = Z
end

begin
prog = mythtv
button = 1_REPLAY
repeat = 0
config = Left
end

begin
prog = mythtv
button = 1_SELECT
repeat = 0
config = Space
end

begin
prog = mythtv
button = 1_0
repeat = 0
config = 0
end

begin
prog = mythtv
button = 1_1
repeat = 0
config = 1
end

begin
prog = mythtv
button = 1_2
repeat = 0
config = 2
end

begin
prog = mythtv
button = 1_3
repeat = 0
config = 3
end

begin
prog = mythtv
button = 1_4
repeat = 0
config = 4
end

begin
prog = mythtv
button = 1_5
repeat = 0
config = 5
end

begin
prog = mythtv
button = 1_6
repeat = 0
config = 6
end

begin
prog = mythtv
button = 1_7
repeat = 0
config = 7
end

begin
prog = mythtv
button = 1_8
repeat = 0
config = 8
end

begin
prog = mythtv
button = 1_9
repeat = 0
config = 9
end 

```

I use a Packard Bell IR Receiver with remote as well as a TiVo remote, so I have two configs in there.

---

