---
title: "Mplayer config"
date: 2009-02-22
forum: Multimedia Software
---

### Post by sn0m on 2009-02-22
hey guys I've changed sth in Mplayer and now video is in fast forward mode, while sound in rnormal speed.
Is there a way to restore original configuration???? otherwise any chance to post your mplayer config file, so i can copy it to mine.
reg
Sokol

---

### Post by stefangr1 on 2009-02-22
These were the default settings on my system, meaning: basically there's no default configuration.

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

# Write your default config options here!

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
ao=alsa,

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

---

### Post by sn0m on 2009-02-22
Mate how about gui.conf file in your .mplayer
I'm sure something changed there.
reg Sokol

---

### Post by benerivo on 2009-02-22
Could you just delete one, or all of your .conf files in ~/.mplayer, then open mplayer to generate new default ones.

---

### Post by sn0m on 2009-02-22
yea done that already, even doing a remove --purge mplayer and re-install, same problem.
In the preference option the FPS is stuck at 00.000 value. I have changed it to 25.000fps and works fine but have to do it manualy each time I play video file as it reverses itself to 00.000 FPS on exit.
Strange, but I think there must be another conf file somewhere else, i just haven't found it.
regards
Sokol

---

### Post by mc4man on 2009-02-22
Look in /etc/mplayer

---

