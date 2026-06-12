---
title: "mplayer couldn't play anything."
date: 2009-01-18
forum: Multimedia Software
---

### Post by Kelen.Chang on 2009-01-18
```
&#9484;&#9472;(Fire@ubuntu:pts/1)&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;(~)&#9472;&#9488;
&#9492;&#9472;(09:44:%)&#9472;&#9472; mplayer Movies/Kung.Fu.Panda.HR-HDTV.AC3.960X540.x264.avi
MPlayer 1.0rc2-4.2.4 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Warning unknown option subfont-autoscale at line 14
Warning unknown option subfont-text-scale at line 18
/usr/share/fonts/msyh075/msyh.ttf doesn't look like a bitmap font description, ignoring.
Cannot load bitmap font: /usr/share/fonts/msyh075/msyh.ttf

Playing Movies/Kung.Fu.Panda.HR-HDTV.AC3.960X540.x264.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [H264]  960x540  24bpp  23.976 fps  1792.3 kbps (218.8 kbyte/s)
Clip info:
Software: VirtualDubMod 1.5.10.1 (Build 2366/Release)
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 320.0 kbit/20.83% (ratio: 40000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
Opening /dev/dvb/adapter0/audio0
DVB AUDIO DEVICE: No such file or directory
AO: [null] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   9.5 (09.5) of 36556.0 (10:09:15.9)  1.3%
```

here is my config
~$ cat /etc/mplayer/mplayer.config
```
#
# MPlayer configuration file
#
# Configuration files are read system-wide from /usr/local/etc/mplayer.conf
# and per user from ~/.mplayer/config, where per-user settings override
# system-wide settings, all of which are overrriden by the command line.
#
# The configuration file settings are the same as the command line
# options without the preceding '-'.
#
# See the CONFIGURATION FILES section in the man page
# for a detailed description of the syntax.


##################
# video settings #
##################

# Specify default video driver (see -vo help for a list).
vo=xv

# Use SDL video with the aalib subdriver by default.
#vo = sdl:aalib

# FBdev driver:
#
# mode to use (read from fb.modes)
#fbmode = 640x480-120
#
# location of the fb.modes file
#fbmodeconfig = /etc/fb.modes

# Specify your monitor timings for the vesa and fbdev video output drivers.
# See /etc/X11/XF86Config for timings. Be careful; if you specify settings
# that exceed the capabilities of your monitor, you may damage it.
#
# horizontal frequency range (k stands for 1000)
#monitor-hfreq = 31.5k-50k,70k
#
# vertical frequency range
#monitor-vfreq = 50-90
#
# dotclock (or pixelclock) range (m stands for 1000000)
#monitor-dotclock = 30M-300M

# Start in fullscreen mode by default.
#fs=yes

# Change to a different videomode when going fullscreen.
#vm=yes

# Override the autodetected color depth, may need 'vm=yes' as well.
#bpp=0

# Enable software scaling (powerful CPU needed) for video output
# drivers that do not support hardware scaling.
#zoom=yes

# standard monitor size, with square pixels
#monitoraspect=4:3

# Use this for a widescreen monitor, non-square pixels.
#monitoraspect=16:9

# Keep the player window on top of all other windows.
#ontop=yes


##################
# audio settings #
##################

# Specify default audio driver (see -ao help for a list).
ao=pulse,alsa,

# Use SDL audio driver with the esd subdriver by default.
#ao = sdl:esd

# Specify the mixer device.
#mixer = /dev/mixer

# Resample the sound to 44100Hz with the lavcresample audio filter.
#af=lavcresample=44100

# Specify default audio codec (see -ac help for a list).
ac=mad,


##################
# other settings #
##################

# Drop frames to preserve audio/video sync.
#framedrop = yes

# Specify your preferred skin here (skins are searched for in
# /usr/local/share/mplayer/skins/<name> and ~/.mplayer/skins/<name>).
#skin = Abyss

# Resample the font alphamap.
# 0     plain white fonts
# 0.75  very narrow black outline (default)
# 1     narrow black outline
# 10    bold black outline
#ffactor = 0.75

# cache settings
#
# Use 8MB input cache by default.
#cache = 8192
#
# Prefill 20% of the cache before starting playback.
#cache-min = 20.0
#
# Prefill 50% of the cache before restarting playback after the cache emptied.
#cache-seek-min = 50

# DVD: Display English subtitles if available.
#slang = en

# DVD: Play English audio tracks if available.
#alang = en


# You can also include other configuration files.
#include = /path/to/the/file/you/want/to/include

#Screensaver support (for non gmplayer)
stop-xscreensaver = "yes"

#Disable joystick support
#It seems to cause very odd problems on laptops
#With accelerometers (See LP: #75925)
nojoystick = yes

```

---

