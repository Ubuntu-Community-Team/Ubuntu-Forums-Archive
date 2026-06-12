---
title: "MPlayer on Ubuntu"
date: 2008-10-04
forum: Multimedia Software
---

### Post by efeurich on 2008-10-04
Hi there,

I would like to install MPlayer but it seems to have some issues with dependencies.
Can anyone give me some pointers on this?

Thanks,

EIF

---

### Post by Drejcek on 2008-10-04
Go "System > Administration > Synaptic Package Manager" and then Search for "mplayer". 


I'll borrow this topic because I have a problem with MPlayer. Subtitles doesn't work like they should. There are some strange letters and it typing all the time "______". I helped myself with this [LINK](http://ubuntuforums.org/archive/index.php/t-77329.html), but there is no effect.

My config file:
```
#==========
# Subtitles
#==========

# VobSubs
#========

# Align subs. (-1: as they want to align themselves)
spualign=-1

# Anti-alias subs. (4: best and slowest)
spuaa=4
# Text-based subtitles
#=====================

# Find subtitle files. (1: load all subs containing movie name)
sub-fuzziness=1

# Set font encoding.
subfont-encoding=unicode

# Set subtitle file encoding.
unicode=yes
utf8=yes

# Resample the font alphamap. (1: narrow black outline)
ffactor=1

# Set subtitle position. (100: as low as possible)
subpos=100

# Set subtitle alignment at its position. (2: bottom)
subalign=2

# Set font size. (2: proportional to movie width)
subfont-autoscale=2

# Set font blur radius. (default: 2)
subfont-blur=2.0

# Set font outline thickness. (default: 2)
subfont-outline=2.0

# Set autoscale coefficient. (default: 5)
subfont-text-scale=4.4

# OSD
#====

# Set autoscale coefficient. (default: 6)
subfont-osd-scale=4.4

#===========
# Appearance
#===========

# Disable screensaver.
stop-xscreensaver=yes

```

I already had MPlayer working normally but I had to format my laptop and now I just can't solve this problem.

---

### Post by Drejcek on 2008-10-04
Anyone?

---

### Post by Drejcek on 2008-10-04
This is just great ](*,):-x:x I finally get normal subtitels and then I got 3 error, close one another open, when I close third error, MPlayer closes too. DAMN!

Here are error:
1) [img]http://shrani.si/f/2y/y8/23FmFiIM/evo-error.png[/img]
2) [img]http://shrani.si/f/1n/10w/2xjSzyLf/error-2.png[/img]
3) [img]http://shrani.si/f/34/ma/4QROnyy4/error3.png[/img]

**[SIZE="5"]PLEASE HELP![/SIZE]**

---

### Post by Yellow Pasque on 2008-10-04
> **efeurich said:**
> Hi there,

I would like to install MPlayer but it seems to have some issues with dependencies.
Can anyone give me some pointers on this?

Thanks,

EIF
What issues are you having with dependencies? Are all the repos enabled in System -> Administration -> Software Sources ?

---

### Post by efeurich on 2008-10-09
@Temüjin; Hi what repos should be installed for MPlayer and how can I check this in Software Sources?
@Drejcek; When i install Mplayer via Synaptic Package Manager wil I get the same problems as you?

---

### Post by efeurich on 2008-10-09
Should i install all the packages in SPM?
There are a lot of them....

EIF

---

### Post by aeiah on 2008-10-09
to the guy with the errors, what version of mplayer are you using?

my subtitle fonts are fine.. this is my mplayer config file:

```

enable_audio_equ = "no"
vo_driver = "gl2"
vo_panscan = "0.000000"
vo_doublebuffering = "yes"
vo_direct_render = "no"
vo_dxr3_device = "/dev/em8300-0"
v_framedrop = "0"
v_flip = "0"
v_ni = "no"
v_idx = "1"
vf_pp = "no"
vf_autoq = "0"
vf_lavc = "no"
ao_driver = "alsa"
ao_volnorm = "yes"
softvol = "no"
ao_surround = "no"
ao_extra_stereo = "no"
ao_extra_stereo_coefficient = "0.000000"
dvd_device = "/dev/cdrom"
cdrom_device = "/dev/cdrom"
osd_level = "3"
sub_auto_load = "yes"
sub_unicode = "no"
***_enabled = "no"
***_use_margins = "no"
***_top_margin = "0"
***_bottom_margin = "0"
sub_pos = "100"
sub_overlap = "no"
font_factor = "0.750000"
font_name = "/usr/share/fonts/truetype/msttcorefonts/Arial.ttf"
font_text_scale = "2.440000"
font_osd_scale = "2.440000"
font_blur = "2.000000"
font_outline = "2.000000"
font_autoscale = "3"
cache = "yes"
cache_size = "320"
playbar = "no"
load_fullscreen = "yes"
show_videowin = "yes"
stopxscreensaver = "yes"
autosync = "no"
autosync_size = "0"
gui_skin = "default"
gui_save_pos = "yes"
gui_main_pos_x = "421"
gui_main_pos_y = "554"
gui_video_out_pos_x = "0"
gui_video_out_pos_y = "0"

```

and efeurich, just install mplayer. all the other bits you need will be installed along with it automatically. a lot of people like smplayer. you may want to install this too although ive never bothered with it myself. its just another front end for mplayer.

---

### Post by efeurich on 2008-10-09
Hi aeiah,

I have followed you advice and just installed Mplayer.
Looks and sounds great.

Thanks,

---

