---
title: "ATI hd 5450 Ubuntu 10.10 can't play videos"
date: 2011-02-16
forum: Multimedia Software
---

### Post by arikkk on 2011-02-16
_Hi guys, i have** ubuntu 10.10 kernel 2.6.35-25**-generic installed , 2GB ram, intel 41g express chipset. Machine is double boot -  Ubuntu and Windows 7_

Today I installed ATI hd 5450, everything works fine on Windows, but I have trouble with playing videos on Ubuntu. I logged in Ubuntu and there was this bold black line in the bottom of the screen (about 1/4 of the screen in total), I reboot and it was there again, so I installed and activated ATI driver System=>administration=>additional drivers
**Installed ATI Catalyst driver**
Reboot and that line was gone, but after a while I noticed that VLC and Movie Player won't play videos, I tried formats like avi, mkv, mp4. There is a** sound** but **no picture.** I can play youtube and other videos in browser (Firefox, Chrome). I tried installing a few other video players but it didn't help. I was able to play videos with integrated video card.

Help me plz!

---

### Post by arikkk on 2011-02-16
I also tried the following commands
dpkg -l | grep -Eo "^.i +linux-(image|headers)[^ ]+" | cut -c 5-^C
sudo apt-get install xserver-xorg-video-ati
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update

and know I can't even get in ATI catalyst control centre

---

### Post by arikkk on 2011-02-16
> **arikkk said:**
> I also tried the following commands
dpkg -l | grep -Eo "^.i +linux-(image|headers)[^ ]+" | cut -c 5-^C
sudo apt-get install xserver-xorg-video-ati
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update

and now I can't even get in ATI catalyst control centre

[I]alright it got worse, can't boot Ubuntu, black screen
[/I]
fixed black screen in recovery mode like this

Removed old driver
sudo apt-get remove fglrx fglrx-amdcccle
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo rm -fr /usr/lib/fglrx
sudo rm -fr /etc/ati
sudo reboot

Installed new one
wget [http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh)
chmod 755 install-fglrx-debian.sh
sudo ./install-fglrx-debian.sh -z
sudo aticonfig -f --initial
sudo reboot

---

### Post by arikkk on 2011-02-16
SOLVED the problem

just had to change mpayer.conf and reboot
**/etc/mplayer/mplayer.conf**   

*uncommented this line  *

[B]#vo=xv,x11

[/B]```
#
# MPlayer configuration file
#
# Configuration files are read system-wide from /etc/mplayer/mplayer.conf
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
vo=xv,x11

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

# Use pulse, then alsa, then SDL video with the aalib subdriver by default.
ao=pulse,alsa,sdl:aalib

# Use SDL audio driver with the esd subdriver by default.
#ao = sdl:esd

# Specify the mixer device.
#mixer = /dev/mixer

# Resample the sound to 44100Hz with the lavcresample audio filter.
#af=lavcresample=44100


##################
# other settings #
##################

stop-xscreensaver=yes

# Pretend to be Window Media Player.
# Fixes playback when playlist and media file use the same URL.
#user-agent=NSPlayer/4.1.0.3856

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

###################
# DVDNAV Settings #
###################
#vc=ffmpeg12,

# You can also include other configuration files.
#include = /path/to/the/file/you/want/to/include

``` [I]
list of Available video output drivers can be found with[/I]
**mplayer -vo help**
[http://vsingleton.blogspot.com/2010/02/failed-to-open-vdpau-backend.html](http://vsingleton.blogspot.com/2010/02/failed-to-open-vdpau-backend.html)

---

