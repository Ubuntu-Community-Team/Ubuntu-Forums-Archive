---
title: "pvr-250 refuses to work"
date: 2009-09-18
forum: Mythbuntu
---

### Post by heran on 2009-09-18
Hi everyone,

This is my first post here. I recently decided to give mythbuntu a try. I find it a verry facinating program. I bought two pvr-250 and other hardware to built a backend and a nice frontend. Thanks to mythbuntu even I who does not have much experience in the innerworkings of linux was able to set it up and it is working beautifully.**Nice,** except one card gives no video; for few seconds there is picture and then it becomes blocky and freezes. The other card is the same except the rev nr, and works verry well. For now I pulled out the good one to make trouble shooting easier. I tried using different pci-slots, reconfiguring the backend with only the bad card. no result. After this I allready run out of sollutions.  Can some one hint me in the good direction ? Using the command mplayer /dev/video0 gives besides crappy video the following output:

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
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
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
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
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
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12 
Cannot sync MAD frame:  1.698 ct:  0.000   1/  1 ??% ??% ??,?% 0 0 
Cannot sync MAD frame:  0.938 ct:  0.004   2/  2 ??% ??% ??,?% 1 0 
Cannot sync MAD frame:  0.898 ct:  0.008   3/  3 ??% ??% ??,?% 2 0 
Cannot sync MAD frame:  0.858 ct:  0.012   4/  4 ??% ??% ??,?% 3 0 
Cannot sync MAD frame:  0.818 ct:  0.016   5/  5 ??% ??% ??,?% 3 0 
Cannot sync MAD frame:  0.738 ct:  0.020   6/  6 ??% ??% ??,?% 4 0 
Cannot sync MAD frame:  0.698 ct:  0.024   7/  7 ??% ??% ??,?% 4 0 
Cannot sync MAD frame:  0.658 ct:  0.028   8/  8 ??% ??% ??,?% 4 0 
Cannot sync MAD frame:  0.618 ct:  0.032   9/  9 ??% ??% ??,?% 4 0 
Cannot sync MAD frame:  0.578 ct:  0.036  10/ 10 ??% ??% ??,?% 4 0 
Cannot sync MAD frame:  0.538 ct:  0.040  11/ 11 ??% ??% ??,?% 4 0 
Cannot sync MAD frame:  0.498 ct:  0.040  12/ 12 ??% ??% ??,?% 4 0 
Cannot sync MAD frame:  0.458 ct:  0.040  13/ 13 ??% ??% ??,?% 4 0 
Cannot sync MAD frame:  0.418 ct:  0.040  14/ 14 64% 18% 18.0% 4 0 
Cannot sync MAD frame:  0.378 ct:  0.040  15/ 15 59% 16% 16.7% 4 0 
Cannot sync MAD frame:  0.338 ct:  0.040  16/ 16 55% 15% 15.6% 4 0 
Cannot sync MAD frame:  0.298 ct:  0.040  17/ 17 52% 14% 14.6% 4 0 
Cannot sync MAD frame:  0.258 ct:  0.040  18/ 18 49% 13% 13.8% 4 0 
Cannot sync MAD frame:  0.778 ct:  0.040  19/ 19 46% 13% 13.0% 4 0 
Cannot sync MAD frame:  0.738 ct:  0.040  20/ 20 43% 12% 12.3% 4 0 
Cannot sync MAD frame:  0.738 ct:  0.040
```

output of dmesg | grep eeprom:

```
dmesg | grep eeprom
[    9.292185] tveeprom 0-0050: Hauppauge model 32034, rev B348, serial# 7110103
[    9.292188] tveeprom 0-0050: tuner model is LG TP18PSB11D (idx 48, type 29)
[    9.292190] tveeprom 0-0050: TV standards PAL(B/G) (eeprom 0x04)
[    9.292192] tveeprom 0-0050: audio processor is MSP3415 (idx 6)
[    9.292194] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
[    9.292196] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter

```

output of dmesg | grep ivtv:

```
dmesg | grep ivtv
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
[  119.729320] ivtv0: Cause: the application is not reading fast enough.
[  119.850773] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[  119.850775] ivtv0: Cause: the application is not reading fast enough.
[  119.970550] ivtv0: All encoder MPG stream buffers are full. Dropping data
```

thanks in advance, any help is wellcome.
ps: sorry for english, it's not my mother tonge.

---

### Post by ian dobson on 2009-09-19
Hi,

For the "All encoder MPG stream buffers are full." you need to add more buffers to the ivtv driver.

Go to the terminal
type :-

sudo echo  "options ivtv enc_mpg_buffers=9 ivtv_yuv_mode=2" > /etc/modprobe.d/ivtv.conf

Then reboot.

Regards
Ian Dobson

---

### Post by heran on 2009-09-19
Hi Ian,

thanks for reply. Entering "sudo echo  "options ivtv enc_mpg_buffers=9 ivtv_yuv_mode=2" > /etc/modprobe.d/ivtv.conf" in a terminal does not work. I get a "permission denied" back from bash. Verry strang?! So I did " sudo nano /etc/modprobe.d/ivtv.conf" and copied in there "options ivtv enc_mpg_buffers=9 ivtv_yuv_mode=2". After restarting and doing mplayer /dev/virdeo0 the video is still the same. Thanks anyway; any more suggestions?

---

### Post by ahood on 2009-09-19
Hi heran,

I don't know if I can help.

The messages above leads me to think that there is an audio issue. That is, a hardware problem with audio. It could be that the problem is with mplayer. I know I have had troubles with mplayer on some systems and had to take care in selecting the video and audio settings with using mplayer. Sometimes I use vlc player and if both programs have problems, then it is likely not a software/application issue, and maybe hardware. If vlc can capture video, but mplayer cannot, then it may suggest an mplayer issue.

Lastly, how are the two tv tuners configured? I have a PVR 250 and I use the MPEG option in the backend and not the v4l driver.

I hope this helps.

---

### Post by heran on 2009-09-20
Thanks ahood,
In backend I allready use the option: ivtv mpeg encoder card... I also tried VLC (selecting right device+tuning to a channel) with the same crappy video as result. Still hoping this is some driver/firmware/software issue.

---

