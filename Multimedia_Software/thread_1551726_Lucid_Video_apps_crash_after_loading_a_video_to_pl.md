---
title: "Lucid: Video apps crash after loading a video to play"
date: 2010-08-12
forum: Multimedia Software
---

### Post by K7AAY on 2010-08-12
Have a Dell Latitude X300 with Intel video. Did the modeset fix to fix video in Lucid.

Video, several weeks after install, now fails; when a file to play is loaded, every video app crashes after sensing the nature of the file. 

Removed video apps with sudo apt-get remove avidemux-plugins-common* avidemux-plugins-gtk* gstreamer0.10-ffmpeg* gstreamer0.10-ffmpeg-dbg* gstreamer0.10-plugins-bad-multiverse* gstreamer0.10-plugins-bad-multiverse-dbg* gstreamer0.10-plugins-ugly-multiverse* gstreamer0.10-plugins-ugly-multiverse-dbg* libavcodec-extra-52* libavformat52* libmjpegtools-1.9* libquicktime-dev* libquicktime1* libx264-85* mozilla-plugin-vlc* remuco-vlc* vlc* vlc-dbg* vlc-nox* vlc-plugin-ggi* vlc-plugin-jack* vlc-plugin-pulse* vlc-plugin-sdl* vlc-plugin-svg* vlc-plugin-svgalib*

unmarked all repositories but for the original (incl. Medibuntu) and then reinstalled. No joy.  Opened up Medibuntu, reinstalled, same problem. 

Tried the fixes outlined in [http://ubuntuforums.org/showthread.php?t=1293760&highlight=video+failure](http://ubuntuforums.org/showthread.php?t=1293760&highlight=video+failure)  and [http://www.ubuntugeek.com/fix-for-vlc-doesnt-play-video-after-ubuntu-9-10-karmic-upgrade.html](http://www.ubuntugeek.com/fix-for-vlc-doesnt-play-video-after-ubuntu-9-10-karmic-upgrade.html) to no avail.

How do I fix this and be able to watch vids again?

Many thanks, all.

---

### Post by Tclarkie on 2010-08-12
what type of video is it, what apps are u using

---

### Post by K7AAY on 2010-08-13
> **Tclarkie said:**
> what type of video is it, what apps are u using

Intel Extreme 2 Graphics, 82852/855GM Integrated Graphics Device, using the i915 driver

VLC 1.06 Goldeneye
totem 2.30.2
GNOME Mplayer 0.9.9.2-1

---

### Post by K7AAY on 2010-08-15
Help?

---

### Post by K7AAY on 2010-08-15
'mplayer -vo x11 /path/to/video' works, BTW - how do I make this fix permanent?

---

### Post by andrew.46 on 2010-08-17
Hi K7AAY,

> **K7AAY said:**
> 'mplayer -vo x11 /path/to/video' works, BTW - how do I make this fix permanent?

Try adding :

```
vo=x11
```

to your $HOME/.mplayer/config file.

Andrew

---

### Post by K7AAY on 2010-08-17
> **andrew.46 said:**
> Hi K7AAY,



Try adding :

```
vo=x11
```

to your $HOME/.mplayer/config file.

Andrew

That works for launching a video from the command line. However, when I double-click on a file to launch it in Mplayer, or launch Mplayer and then open a file, the problem persists. That's very preferable, as when I launch a video from the command line, I have no controls for mPlayer; no way to pause, adjust volume, move forward or back. 

Here is the conf.gui file:

enable_audio_equ = "no"
vo_driver = "x11"
vo_panscan = "0.000000"
vo_doublebuffering = "yes"
vo_direct_render = "no"
v_framedrop = "0"
v_flip = "0"
v_ni = "no"
v_idx = "-1"
vf_pp = "no"
vf_autoq = "0"
vf_lavc = "no"
ao_driver = "pulse"
ao_volnorm = "no"
softvol = "no"
ao_surround = "no"
ao_extra_stereo = "no"
ao_extra_stereo_coefficient = "1.000000"
dvd_device = "/dev/dvd"
cdrom_device = "/dev/cdrom"
osd_level = "1"
sub_auto_load = "yes"
sub_unicode = "no"
***_enabled = "no"
***_use_margins = "no"
***_top_margin = "0"
***_bottom_margin = "0"
sub_pos = "100"
sub_overlap = "no"
font_factor = "0.750000"
font_text_scale = "3.500000"
font_osd_scale = "4.000000"
font_blur = "2.000000"
font_outline = "2.000000"
font_autoscale = "3"
cache = "no"
cache_size = "2048"
playbar = "no"
load_fullscreen = "no"
show_videowin = "yes"
stopxscreensaver = "yes"
autosync = "no"
autosync_size = "0"
gui_skin = "default"
gui_save_pos = "yes"
gui_main_pos_x = "643"
gui_main_pos_y = "648"
gui_video_out_pos_x = "538"
gui_video_out_pos_y = "48"
equ_band_00 = "0.000000"
equ_band_01 = "0.000000"
equ_band_02 = "0.000000"
equ_band_03 = "0.000000"
equ_band_04 = "0.000000"
equ_band_05 = "0.000000"
equ_band_06 = "0.000000"
equ_band_07 = "0.000000"
equ_band_08 = "0.000000"
equ_band_09 = "0.000000"
equ_band_10 = "0.000000"
equ_band_11 = "0.000000"
equ_band_12 = "0.000000"
equ_band_13 = "0.000000"
equ_band_14 = "0.000000"
equ_band_15 = "0.000000"
equ_band_16 = "0.000000"
equ_band_17 = "0.000000"
equ_band_18 = "0.000000"
equ_band_19 = "0.000000"
equ_band_20 = "0.000000"
equ_band_21 = "0.000000"
equ_band_22 = "0.000000"
equ_band_23 = "0.000000"
equ_band_24 = "0.000000"
equ_band_25 = "0.000000"
equ_band_26 = "0.000000"
equ_band_27 = "0.000000"
equ_band_28 = "0.000000"
equ_band_29 = "0.000000"
equ_band_30 = "0.000000"
equ_band_31 = "0.000000"
equ_band_32 = "0.000000"
equ_band_33 = "0.000000"
equ_band_34 = "0.000000"
equ_band_35 = "0.000000"
equ_band_36 = "0.000000"
equ_band_37 = "0.000000"
equ_band_38 = "0.000000"
equ_band_39 = "0.000000"
equ_band_40 = "0.000000"
equ_band_41 = "0.000000"
equ_band_42 = "0.000000"
equ_band_43 = "0.000000"
equ_band_44 = "0.000000"
equ_band_45 = "0.000000"
equ_band_46 = "0.000000"
equ_band_47 = "0.000000"
equ_band_48 = "0.000000"
equ_band_49 = "0.000000"
equ_band_50 = "0.000000"
equ_band_51 = "0.000000"
equ_band_52 = "0.000000"
equ_band_53 = "0.000000"
equ_band_54 = "0.000000"
equ_band_55 = "0.000000"
equ_band_56 = "0.000000"
equ_band_57 = "0.000000"
equ_band_58 = "0.000000"
equ_band_59 = "0.000000"

---

### Post by andrew.46 on 2010-08-17
Hi K7AAY,

I presume you are using the default gui for MPlayer called GMPlayer? Might be easier to use SMPlayer and adjust the required video settings from Preferences:

```
sudo apt-get install smplayer
```

BTW the commandline player has all the commands you would ever need, just need to be entered via the keyboard.

Andrew

---

### Post by K7AAY on 2010-08-17
> **andrew.46 said:**
> Hi K7AAY,

I presume you are using the default gui for MPlayer called GMPlayer? Might be easier to use SMPlayer and adjust the required video settings from Preferences:

```
sudo apt-get install smplayer
```
Worked! Thank you.

> BTW the commandline player has all the commands you would ever need, just need to be entered via the keyboard.

Andrew Thank you for that tip as well.

Now, how can I fix the broken driver? This thing _did_ work, once, without having to use the slow x11 driver.....

---

### Post by andrew.46 on 2010-08-18
Hi K7AAY,

> **K7AAY said:**
> Now, how can I fix the broken driver? This thing _did_ work, once, without having to use the slow x11 driver.....

Good to hear that at least you have playback now, not so sure about the broken driver though, sorry...

Andrew

---

### Post by Linuxforall on 2010-08-18
Add ubuntu x ppa, in terminal sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update
sudo apt-get upgrade

This will update your Intel driver to latest thereby giving you better compatibility.

---

### Post by ihiribar on 2010-09-18
This didn't work for me. I used the package "855gm-fix-exp-dkms" from 
[https://launchpad.net/~glasen/+archive/855gm-fix](https://launchpad.net/~glasen/+archive/855gm-fix)

to install it:

sudo add-apt-repository glasen/855gm-fix
sudo apt-get update
sudo apt-get install 855gm-fix-exp-dkms

if the system is unstable after this procedure you can instead install the more stable package

sudo apt-get remove 855gm-fix-exp-dkms
sudo apt-get install 855gm-fix-dkms

This fixes the issues which apparently stem from kernel modesetting.

---

