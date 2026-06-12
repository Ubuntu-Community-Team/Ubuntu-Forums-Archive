---
title: "Trying to figure out the best 5.1 Surround Setup for HTPC"
date: 2012-07-16
forum: Multimedia Software
---

### Post by Gremlyn1 on 2012-07-16
My HTPC has been running on Ubuntu 11.10 (plan to upgrade to 12.04 some day, but too many things broke right off the bat for me to want to deal with it now). I use XBMC and MythTV, and have an nVidia GT520 video card that is handling the audio via HDMI as well.

For too long I was only able to play 2.0 PCM through my old receiver, as 2.0 PCM was all it could handle, and I could never get any of the passthroughs to work right. I recently bought a new receiver that handles 5.1 PCM, as well as all the other audio modes (DTS, AC3, etc). I first set the system up to be able to use the surround sound with the a52 plugin, but after doing some reading there may be better ways to do this. I'd be fine with letting the receiver handle the decoding and whatnot.

I have tried setting XBMC to use the nVidia hdmi for both the Audio Device and Passthrough, and tried the AC3/DTS capable receiver settings, all with no luck getting sound. The a52 plugin works well enough, but I lose it every time I suspend the system, and I don't want to have to reboot every time I wake it up. So if there is a better way, please do tell! None of my searching has come up with anything definitive. I have seen many suggestions and things to try, but having already installed the a52 plugin, I'd rather not clutter the system with more hacks and trials until I can no longer sort out what the hell is going on with it.

The extreme option could just be to remove PulseAudio. This is a dedicated HTPC, so whatever gets the sound working properly is great!

aplay -L
```

default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Hardware device with all software conversions
a52:CARD=PCH
    HDA Intel PCH
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
a52:CARD=NVidia
    HDA NVidia

```

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

sudo dmesg | grep HDMI
```

[   13.492753] HDMI status: Pin=4 Presence_Detect=0 ELD_Valid=0
[   13.516748] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   13.532811] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input7
[   13.532874] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[   16.397961] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[   16.408755] HDMI status: Pin=5 Presence_Detect=1 ELD_Valid=0
[   16.416761] HDMI hot plug event: Pin=5 Presence_Detect=0 ELD_Valid=1
[   16.424762] HDMI status: Pin=5 Presence_Detect=1 ELD_Valid=1
[   17.216787] HDMI: detected monitor TX-SR313
[   17.216788]      at connection type HDMI
[   17.216791] HDMI: available speakers: FL/FR LFE FC RL/RR
[   17.216795] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200 176400 192000 384000, bits = 16 20 24
[   17.216799] HDMI: supports coding type LPCM: channels = 6, rates = 44100 48000 88200 176400 192000 384000, bits = 16 20 24
[   17.216801] HDMI: supports coding type AC-3: channels = 8, rates = 44100 48000 88200, max bitrate = 640000
[   17.216804] HDMI: supports coding type DTS: channels = 8, rates = 48000 88200, max bitrate = 1536000
[   17.216806] HDMI: supports coding type DSD (One Bit Audio): channels = 6, rates = 48000
[   17.216808] HDMI: supports coding type E-AC-3/DD+ (Dolby Digital Plus): channels = 8, rates = 48000 88200
[   17.216811] HDMI: supports coding type DTS-HD: channels = 8, rates = 48000 88200 176400 192000 384000
[   17.216813] HDMI: supports coding type MLP (Dolby TrueHD): channels = 8, rates = 88200 192000

```

---

### Post by beandog on 2012-07-17
Try playing something with an Dolby Digital track through your receiver to verify it is streaming properly:

mplayer movie.mp4 -ac hwac3

---

### Post by Gremlyn1 on 2012-07-17
> **beandog said:**
> Try playing something with an Dolby Digital track through your receiver to verify it is streaming properly:

mplayer movie.mp4 -ac hwac3

Just tried this and got no sound.

---

### Post by Gremlyn1 on 2012-07-17
I just tried it without the '-ac hwac3' and still go no sound. I would have assumed the default output would give me sound, though I'm not entirely sure as I'm not familiar with mplayer from the command line.

EDIT: I looked at the mplayer man page, and tried to play a little. I set the audio output for pulse with no code, got no sound, I tried setting is to a52 (since I have that plugin installed and working in XBMC), and apparently that has to be configured when mplayer is installed so it didn't work either.

EDIT 2: Ok, I got sound in mplayer. I have to run it as mplayer movie.mkv -ao alsa:noblock:device=hw=1.3 -ac hwac3. If I left off the -ac hwac3 I get sound as well, but obviously not Dolby Digital. I'm not sure if I need the noblock on there, it seems to work either way. I'm not sure if was entirely right though, so it seemed to think I couldn't handle multichannel playback still. See below for mplayer's output:

```

mplayer: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
MPlayer SVN-r33713-4.6.1 (C) 2000-2011 MPlayer Team

Playing 300 (2006).mkv.
libavformat file format detected.
[matroska,webm @ 0xb15380] max_analyze_duration reached
[matroska,webm @ 0xb15380] Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (ac3), -aid 0, -alang eng
[lavf] stream 2: subtitle (text), -sid 0, -slang eng
VIDEO:  [H264]  1920x800  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in ./
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Forced audio codec: hwac3
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
hwac3: switched to AC3, 640000 bps, 48000 Hz

AUDIO: 48000 Hz, 2 ch, ac3be, 640.0 kbit/41.67% (ratio: 80000->192000)
Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
==========================================================================
[AO_ALSA] alsa-lib: conf.c:4514:(parse_args) Unknown parameter AES0
[AO_ALSA] alsa-lib: conf.c:4647:(snd_config_expand) Parse arguments error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM hw:1,3,AES0=6
[AO_ALSA] Format ac3be is not supported by hardware, trying default.
AO: [alsa] 48000Hz 2ch ac3le (2 bytes per sample)
Starting playback...
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Movie-Aspect is 2.40:1 - prescaling to correct movie aspect.
VO: [vdpau] 1920x800 => 1920x800 Planar YV12 
A: 125.3 V: 125.2 A-V:  0.000 ct:  0.042   0/  0 41%  2%  0.8% 11 0 


MPlayer interrupted by signal 2 in module: decode video
A: 125.3 V: 125.3 A-V:  0.000 ct:  0.042   0/  0 41%  2%  0.8% 11 0 

Exiting... (Quit)

```

It did seem to be in full surround, but the output above talks about not supporting it and switching down to 2ch.

---

