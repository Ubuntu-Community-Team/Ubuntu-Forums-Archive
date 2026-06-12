---
title: "one of two pvr-250's makes mplayer crash with crappy video"
date: 2009-09-18
forum: Multimedia Software
---

### Post by heran on 2009-09-18
Hi all,
I am new to this and any forum , so I will introduce myself a bit. Well, since a couple of years I made the switch from windows 98 to ubuntu. Clicking around  email and web surfing was pretty easy;  So I nerver got into the innerworkings of the system. Troubleshooting problems  means a bit :confused:.  

Recently I got two hauppauge pvr-250 cards. So I decided to built a mythbuntu system (as a learning project.....and to impress my house mates :guitar:). Everything works accept one hauppauge card refuses to give video. I pult the  card that works out and tried the faulrty one in different pci slots with the command: mplayer /dev/video0 and cat /dev/video0 > test.mpg. Mplayer outputs stuff I don't understand:

```
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Sempron(tm) Processor LE-1300 (Family: 15, Model: 127, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
E: context.c: waitpid(): No child processes
AO: [pulse] Failed to connect to server: Internal error
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
[AO_ALSA] Playback open error: No such file or directory
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
[AO_ALSA] Playback open error: No such file or directory
[AO ESD] esd_open_sound failed: Connection timed out
E: context.c: waitpid(): No child processes
AO: [pulse] Failed to connect to server: Internal error
[JACK] cannot open server
ao_nas: init(): Can't open nas audio server -> nosound
[AO SDL] Samplerate: 48000Hz Channels: Stereo Format s16le
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
[AO SDL] Unable to open audio: No available audio device
AL lib: alsa.c:785: no playback cards found...
AL lib: alsa.c:853: no capture cards found...
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
AL lib: alsa.c:344: Could not open playback device 'default': No such file or directory
AL lib: oss.c:179: Could not open /dev/dsp: No such file or directory
[OpenAL] could not open device
Opening /dev/dvb/adapter0/audio0
DVB AUDIO DEVICE: No such file or directory
AO: [null] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12 
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12 
missing marker bit!-V:  9.135 ct:  1.564 416/416  1%  0% 12.7% 0 0 
Warning! FPS changed 25.000 -> 0.000  (25.000000) [0]  % 12.2% 0 0 
Warning! FPS changed 0.000 -> 25.000  (-25.000000) [3]    0.0% 1 0 
A:  33.1 V:   9.0 A-V: 24.113 ct:  2.280 601/601  0%  0%  0.0% 1 0 
```
With dmesg | grep ivtv again lots of errors:

```
[    9.241729] ivtv:  Start initialization, version 1.4.0
[    9.241825] ivtv0: Initializing card #0
[    9.241828] ivtv0: Autodetected Hauppauge card (cx23416 based)
[    9.242984] ivtv 0000:01:08.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
[    9.242992] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[    9.292198] ivtv0: Autodetected Hauppauge WinTV PVR-250
[    9.393378] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[    9.518653] msp3400 0-0040: MSP3415G-B8 found @ 0x80 (ivtv i2c driver #0)
[    9.519900] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[    9.549811] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[    9.549849] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[    9.549886] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[    9.549947] ivtv0: Registered device video24 for encoder PCM (320 kB)
[    9.549949] ivtv0: Initialized card #0: Hauppauge WinTV PVR-250
[    9.549983] ivtv:  End initialization
[   26.556018] ivtv 0000:01:08.0: firmware: requesting v4l-cx2341x-enc.fw
[   26.635772] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   26.832134] ivtv0: Encoder revision: 0x02060039
[  118.159370] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[  118.159374] ivtv0: Cause: the application is not reading fast enough.
[  118.287900] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[  118.287904] ivtv0: Cause: the application is not reading fast enough.
[  118.408729] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[  118.408732] ivtv0: Cause: the application is not reading fast enough.
[  118.837448] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[  118.837452] ivtv0: Cause: the application is not reading fast enough.
[  119.005675] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[  119.005678] ivtv0: Cause: the application is not reading fast enough.
[  119.248143] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[  119.248146] ivtv0: Cause: the application is not reading fast enough.
[  119.370000] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[  119.370003] ivtv0: Cause: the application is not reading fast enough.
[  119.490455] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[  119.490457] ivtv0: Cause: the application is not reading fast enough.
[  119.729317] ivtv0: All encoder MPG stream buffers are full. Dropping data.
............
```Both cards have a different revision number: the working one is PAL-B/G 32034 rev B148, the faulty one is PAL-B/G 32034 REV B348. Maybe some driver or firmware is not loaded correctly. Could someone please  hint me in the good direction? Eternal fame would be your share:KS.

Thank you in advance

---

### Post by bsntech on 2009-09-18
Howdy -

Do you have your MythTV configured as of yet?  In the back-end of MythTV, does it show that you have a video card on /dev/video0 and /dev/video1?  From the ivtv logs, it seems like it is recognizing one card but possibly not a second (unless this is the log from where you only had the one installed that isn't working).

It is also possible that it isn't showing any video/audio in mplayer because the tuner isn't currently set to a channel.  This is where you can get it setup in MythTV and check it.  Use the MythTV back-end to setup the PVR-150 as the MPEG-2 card.  Then scan for channels and see if that works.

After the channels are saved, go into the MythTV frontend and hit the Watch TV and see if you get anything from it.

The mplayer log shows that it is picking up an MPEG-2 stream along with stereo mode audio from /dev/video0.

---

### Post by heran on 2009-09-18
thanks for reply,

The log is indeed after I pulled out the good one.
Even After reconfiguring the backend with only the bad card inserted, the result is the same: no / unwatchable video.

---

