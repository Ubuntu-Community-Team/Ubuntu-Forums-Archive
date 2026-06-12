---
title: "MPlayer Audio issues.... desync"
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by tenchu77491 on 2007-12-09
**Ubuntu 7.10 - AMD64**

Okay, today I got MPlayer to work great in nearly everything. I hit a desync problem in non-avi videos, and I did some research in the forum and google and found a solution that worked for nearly all of the videos I tested. There are still some random .mpeg and .flv videos that are desync. I have a theory the problem is in my config, or in the command I use to run all of my videos..... 

To begin with my MPlayer would not open files, so I created a custom MPlayer launch that was "mplayer %M" so I could select that to open files, and then double click my files and poof, they open in mplayer. I found out about some -fps command, should I put that in the command for all of my videos? Would that do anything? Is there more I should add to it for a standard launcher? 

Here is my mplayer.conf if you can find any problems that may lead to some desyncing let me know, or if you find anything I should add or remove let me know. I will mark in bold what I found on the forum that helped me fix the desync problem in most videos. 



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
aspect=16:9

# Keep the player window on top of all other windows.
#ontop=yes


##################
# audio settings #
##################

[B]mc=0 # fix sync problem... maybe?
autosync=0 # fix sync problem... maybe?[/B]

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
framedrop = yes

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

### Post by eye208 on 2007-12-10
From [http://www.linuxtutorialblog.com/post/tutorial-playing-around-with-mplayer](http://www.linuxtutorialblog.com/post/tutorial-playing-around-with-mplayer):
> Correcting bad audio/video sync

Some videos (mainly flv files) are encoded in a horrible way, and MPlayer will have enormous trouble with the A/V (Audio/Video) sync. There are pretty much two possibilities in this case:

    * MPlayer is trying to fix it but the sync is worsening too fast
    * MPlayer is trying to fix something that's already right and therefore pushes the sync away unnecessarily

In the first case, you should allow MPlayer to try harder to fix the sync:

    [rechosen@localhost ~]$ mplayer -autosync 30 -mc 2.0 <somefile>

In the second case, you shouldn't allow MPlayer to fix anything when it comes to the sync:

    [rechosen@localhost ~]$ mplayer -autosync 0 -mc 0 <somefile>

You might wonder what those options mean. Well, setting autosync to a positive value allows MPlayer to gradually adapt its A/V correction algorithm. The higher the value, the faster MPlayer will try to correct it. The mc option specifies how many seconds MPlayer may correct every frame. Setting it to a high value (like 2.0) practically allows MPlayer to do whatever it thinks it should to correct the A/V sync. Setting it to 0 stops MPlayer from trying anything when it comes to syncing.
Setting mc and autosync in the config file may not always give you the best results. In fact mc=0 will prevent any sync correction.

---

### Post by tenchu77491 on 2007-12-10
I tried mc at 2.0 and other values and it slows down the .flv video and causes a bigger desync. Setting it to 0 makes all of my .flv files play fine but causes a very very slight desync in *some* .mpeg files.... any ideas?

---

### Post by tenchu77491 on 2007-12-10
Bump.....

---

