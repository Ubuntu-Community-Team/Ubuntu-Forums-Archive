---
title: "Command to change PVR-150 from tuner to composite in myplayer or cat"
date: 2008-07-04
forum: Multimedia Software
---

### Post by Mysticle31 on 2008-07-04
I have Ubuntu Gutsy and a PVR-150 and I have a cable box hooked up to composite in and a VCR hooked to the tuner.  What command can I issue that will make Mplayer or cat > XXX.mpg to switch to the tuner side and back to the composite side?

I'm slowly investigating converting my VHS tapes to Mpeg files.







Also, does this look right?  I have a 2.8ghz P4 800mhz fsb - not a speed demon anymore but surely capable to do this.
> 
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Playing /dev/video0.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  8000.0 kbps (1000.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
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
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
A:   9.6 V:   9.1 A-V:  0.556 ct: -0.367 249/249 11%  1% 56.9% 50 0 

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.

---

### Post by Porpoise on 2008-07-04
Hi, 

This is the very issue I've been working on. [http://ubuntuforums.org/showthread.php?t=763698&page=3](http://ubuntuforums.org/showthread.php?t=763698&page=3) Post #23

You can change between inputs using "v4l2-input" - as per the above post. There is also the very useful TV-Viewer application for a simple way of switching TV channels using a GUI rather than the command-line. The application writer hasn't yet incorporated a working RECORD function yet though.

Edit:
Forgot to mention, if you want to preview what you're recording, let the recording go for about 30 seconds then open the file (the one you're recording) in Mplayer. I haven't yet sussed out the commands to give VLC to get it to preview the stream at the same time as it's recording it.

---

### Post by Mysticle31 on 2008-07-04
What is this v4l command?  I can't seem to find a way to install it.  I can use MythTV to just fine to change inputs.

---

### Post by Porpoise on 2008-07-05
> **Mysticle31 said:**
> What is this v4l command?  I can't seem to find a way to install it.  I can use MythTV to just fine to change inputs.

v4l2 (vee four el two)
Video 4 Linux. (v2) - it's a driver not a command.

v4l2-ctl is used to get/set the driver parameters/settings

To list the parameters:
```

root@SUPER-ROCK:/home/steve# v4l2-ctl
Usage:
Common options:
  --all              display all information available
  -B, --get-fmt-sliced-vbi
             query the sliced VBI capture format [VIDIOC_G_FMT]
  -b, --set-fmt-sliced-vbi=<mode>
                     set the sliced VBI capture format to <mode> [VIDIOC_S_FMT]
                     <mode> is a comma separated list of:
                     off:      turn off sliced VBI (cannot be combined with other modes)
                     teletext: teletext (PAL/SECAM)
                     cc:       closed caption (NTSC)
                     wss:      widescreen signal (PAL/SECAM)
                     vps:      VPS (PAL/SECAM)
  -C, --get-ctrl=<ctrl>[,<ctrl>...]
                     get the value of the controls [VIDIOC_G_EXT_CTRLS]
  -c, --set-ctrl=<ctrl>=<val>[,<ctrl>=<val>...]
                     set the controls to the values specified [VIDIOC_S_EXT_CTRLS]
  -D, --info         show driver info [VIDIOC_QUERYCAP]
  -d, --device=<dev> use device <dev> instead of /dev/video0
                     if <dev> is a single digit, then /dev/video<dev> is used
  -F, --get-freq     query the frequency [VIDIOC_G_FREQUENCY]
  -f, --set-freq=<freq>
                     set the frequency to <freq> MHz [VIDIOC_S_FREQUENCY]
  -h, --help         display this help message
  -I, --get-input    query the video input [VIDIOC_G_INPUT]
  -i, --set-input=<num>
                     set the video input to <num> [VIDIOC_S_INPUT]
  -l, --list-ctrls   display all controls and their values [VIDIOC_QUERYCTRL]
  -L, --list-ctrls-menus
             display all controls, their values and the menus [VIDIOC_QUERYMENU]
  -N, --list-outputs display video outputs [VIDIOC_ENUMOUTPUT]
  -n, --list-inputs  display video inputs [VIDIOC_ENUMINPUT]
  -O, --get-output   query the video output [VIDIOC_G_OUTPUT]
  -o, --set-output=<num>
                     set the video output to <num> [VIDIOC_S_OUTPUT]
  -S, --get-standard
                     query the video standard [VIDIOC_G_STD]
  -s, --set-standard=<num>
                     set the video standard to <num> [VIDIOC_S_STD]
                     <num> can be a numerical v4l2_std value, or it can be one of:
                     pal-X (X = B/G/H/N/Nc/I/D/K/M/60) or just 'pal' (V4L2_STD_PAL)
                     ntsc-X (X = M/J/K) or just 'ntsc' (V4L2_STD_NTSC)
                     secam-X (X = B/G/H/D/K/L/Lc) or just 'secam' (V4L2_STD_SECAM)
  --list-standards   display supported video standards [VIDIOC_ENUMSTD]
  -T, --get-tuner    query the tuner settings [VIDIOC_G_TUNER]
  -t, --set-tuner=<mode>
                     set the audio mode of the tuner [VIDIOC_S_TUNER]
                     Possible values: mono, stereo, lang2, lang1, bilingual
  --list-formats     display supported video formats [VIDIOC_ENUM_FMT]
  -V, --get-fmt-video
                  query the video capture format [VIDIOC_G_FMT]
  -v, --set-fmt-video=width=<w>,height=<h>
                     set the video capture format [VIDIOC_S_FMT]
  --verbose          turn on verbose ioctl error reporting.

Uncommon options:
  --get-fmt-video-out
                  query the video output format [VIDIOC_G_FMT]
  --set-fmt-video-out=width=<w>,height=<h>
                     set the video output format [VIDIOC_S_FMT]
  --get-fmt-overlay
                  query the video overlay format [VIDIOC_G_FMT]
  --get-fmt-output-overlay
                  query the video output overlay format [VIDIOC_G_FMT]
  --set-fmt-output-overlay=chromakey=<key>,global_alpha=<alpha>
                  set the video output overlay format [VIDIOC_S_FMT]
  --get-sliced-vbi-cap
             query the sliced VBI capture capabilities [VIDIOC_G_SLICED_VBI_CAP]
  --get-sliced-vbi-out-cap
             query the sliced VBI output capabilities [VIDIOC_G_SLICED_VBI_CAP]
  --get-fmt-sliced-vbi-out
             query the sliced VBI output format [VIDIOC_G_FMT]
  --set-fmt-sliced-vbi-out=<mode>
                     set the sliced VBI output format to <mode> [VIDIOC_S_FMT]
                     <mode> is a comma separated list of:
                     off:      turn off sliced VBI (cannot be combined with other modes)
                     teletext: teletext (PAL/SECAM)
                     cc:       closed caption (NTSC)
                     wss:      widescreen signal (PAL/SECAM)
                     vps:      VPS (PAL/SECAM)
  --get-fmt-vbi      query the VBI capture format [VIDIOC_G_FMT]
  --get-fmt-vbi-out  query the VBI output format [VIDIOC_G_FMT]
  --overlay=<on>     turn overlay on (1) or off (0) (VIDIOC_OVERLAY)
  --get-fbuf         query the overlay framebuffer data [VIDIOC_G_FBUF]
  --set-fbuf=chromakey=<0/1>,global_alpha=<0/1>,local_alpha=<0/1>,local_inv_alpha=<0/1>
             set the overlay framebuffer [VIDIOC_S_FBUF]
  --get-cropcap      query the crop capabilities [VIDIOC_CROPCAP]
  --get-crop         query the video capture crop window [VIDIOC_G_CROP]
  --set-crop=top=<x>,left=<y>,width=<w>,height=<h>
                     set the video capture crop window [VIDIOC_S_CROP]
  --get-cropcap-output
                     query the crop capabilities for video output [VIDIOC_CROPCAP]
  --get-crop-output  query the video output crop window [VIDIOC_G_CROP]
  --set-crop-output=top=<x>,left=<y>,width=<w>,height=<h>
                     set the video output crop window [VIDIOC_S_CROP]
  --get-cropcap-overlay
                     query the crop capabilities for video overlay [VIDIOC_CROPCAP]
  --get-crop-overlay query the video overlay crop window [VIDIOC_G_CROP]
  --set-crop-overlay=top=<x>,left=<y>,width=<w>,height=<h>
                     set the video overlay crop window [VIDIOC_S_CROP]
  --get-cropcap-output-overlay
                     query the crop capabilities for video output overlays [VIDIOC_CROPCAP]
  --get-crop-output-overlay
                     query the video output overlay crop window [VIDIOC_G_CROP]
  --set-crop-output-overlay=top=<x>,left=<y>,width=<w>,height=<h>
                     set the video output overlay crop window [VIDIOC_S_CROP]
  --get-audio-input  query the audio input [VIDIOC_G_AUDIO]
  --set-audio-input=<num>
                     set the audio input to <num> [VIDIOC_S_AUDIO]
  --get-audio-output query the audio output [VIDIOC_G_AUDOUT]
  --set-audio-output=<num>
                     set the audio output to <num> [VIDIOC_S_AUDOUT]
  --list-audio-outputs
                     display audio outputs [VIDIOC_ENUMAUDOUT]
  --list-audio-inputs
                     display audio inputs [VIDIOC_ENUMAUDIO]

Expert options:
  --streamoff        turn the stream off [VIDIOC_STREAMOFF]
  --streamon         turn the stream on [VIDIOC_STREAMOFF]
  --log-status       log the board status in the kernel log [VIDIOC_LOG_STATUS]
root@SUPER-ROCK:/home/steve# 


```

---

### Post by Mysticle31 on 2008-07-05
hmm.  I have the v4l2-ctrl but the v4l2-input command I get command not found

> steve@Desktop:~$ v4l2-input
bash: v4l2-input: command not found


Is it the v4l driver that I use when I say cat /dev/video0 > XXXX.mpg?

---

### Post by Porpoise on 2008-07-06
> **Mysticle31 said:**
> hmm.  I have the v4l2-ctrl but the v4l2-input command I get command not found


Sorry, that's my fault - confusing you with my thought processes.

The command is:
v4l2-ctl
the parameter is 
-input

So, the complete command with parameter is:
v4l2-ctl --set-input=0   (for Tuner 1)
v4l2-ctl --set-input=1   (for S-Video 1)
v4l2-ctl --set-input=2   (for Composite 1)
v4l2-ctl --set-input=3   (for S-Video 2)
v4l2-ctl --set-input=4   (for Composite 2)

NB: The comments in brackets are not part of the command - that's just so you know which input number relates to which input on the card. 

> 
Is it the v4l driver that I use when I say cat /dev/video0 > XXXX.mpg?
I believe so, and the "video0" signal will be from whichever input has been previously selected by <v4l2-ctl --set-input=X>

So, if you wish to use Composite 1 input to record with "cat", you would do the following:

v4l2-ctl --set-input=2
cat /dev/video0 > XXXX.mpg

then, to switch back to "Tuner 1":

v4l2-ctl --set-input=0

I hope that makes it a bit clearer for you :)

---

### Post by Porpoise on 2008-07-06
As an alternative/addition to above, I've also now figured out the command to enable VLC to display the stream whilst recording:

```
 vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout '#duplicate{dst=display,dst=std{access=file,mux=ts,dst="/home/steve/Desktop/raid-partition/DVCR/filename.mpg"}}'
```(Please note, although it may line-wrap here, the command is actually all on one line)

Obviously, you will need to have set the "input" beforehand and, if using Tuner 1 input, selected the relevant Channel Frequency. So, by way of example, if you are in the UK (PAL) and wish to record from BBC1:

```
v4l2-ctl --set-input=0
v4l2-ctl -f 711.250
vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout '#duplicate{dst=display,dst=std{access=file,mux=ts,dst="/home/steve/Desktop/raid-partition/DVCR/filename.mpg"}}'
```

I hope that might be helpful to someone.

---

### Post by Mysticle31 on 2008-07-06
Very cool - thank you much.

Can Mplayer or v4l deinterlace? Do I have any control over the quality of the mpeg file if I use cat /dev/video0 > XXXX.mpg to make a file or is it just whatever the hardware encoder puts out?

I ask because I am about ready to start making mpegs of my VHS tapes.

I plan on playing with videolan later.  I hope to run a VCR or record player over the network occasionally to different sound systems around the house wherever I want it.

Here is another stupid question.  Why do I have a Composite 1 and Composite 2 and Tuner 1 and Tuner 2 and SVideo1 and Svideo2 when my card has a composite input and a tuner input?

---

### Post by txcrackers on 2008-07-06
You could also install MythTV and use it to control the inputs, manage your recordings, etc.

---

### Post by Porpoise on 2008-07-07
> **Mysticle31 said:**
> Very cool - thank you much.

Can Mplayer or v4l deinterlace? Do I have any control over the quality of the mpeg file if I use cat /dev/video0 > XXXX.mpg to make a file or is it just whatever the hardware encoder puts out?

I ask because I am about ready to start making mpegs of my VHS tapes.

I plan on playing with videolan later.  I hope to run a VCR or record player over the network occasionally to different sound systems around the house wherever I want it.
VLC has deinterlace, I don't think Mplayer has
> 
Here is another stupid question.  Why do I have a Composite 1 and Composite 2 and Tuner 1 and Tuner 2 and SVideo1 and Svideo2 when my card has a composite input and a tuner input?
Pass? Phone a friend? Ask the audience? :-k

---

### Post by DaveQB on 2009-10-05
> **Mysticle31 said:**
> Very cool - thank you much.

Can Mplayer or v4l deinterlace? Do I have any control over the quality of the mpeg file if I use cat /dev/video0 > XXXX.mpg to make a file or is it just whatever the hardware encoder puts out?

I ask because I am about ready to start making mpegs of my VHS tapes.

I plan on playing with videolan later.  I hope to run a VCR or record player over the network occasionally to different sound systems around the house wherever I want it.

Here is another stupid question.  Why do I have a Composite 1 and Composite 2 and Tuner 1 and Tuner 2 and SVideo1 and Svideo2 when my card has a composite input and a tuner input?


I too am interested in that. The quality isn't the best, not as good as capturing with a non-hardware encoder chipped card. So I am fearing the default compression level is too high. 

How can one set the compression level? I am looking at using mencoder but I can't even get mplayer to play with pcr:// [even though it can play running 'mplayer /dev/video0']

Anyone have the PVR-350 working with mencoder or some other capturing software?

Thsanks

---

