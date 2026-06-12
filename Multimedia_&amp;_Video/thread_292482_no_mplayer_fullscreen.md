---
title: "no mplayer fullscreen"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by stevieb on 2006-11-03
hello,

trying to play an avi file in mplayer; on start i get the following error:
```
Requested audio codec family [mp3] (afm=mp3lib) not available.  Enable it at compilation.  
```

mplayer was installed with automatix; running edgy; mplayer gui.conf reads:

```
enable_audio_equ = "no"
vo_driver = "x11"
vo_panscan = "0.000000"
vo_doublebuffering = "yes"
vo_direct_render = "no"
vo_dxr3_device = "/dev/em8300-0"
v_framedrop = "0"
v_flip = "0"
v_ni = "no"
v_idx = "-1"
vf_pp = "no"
vf_autoq = "0"
vf_lavc = "no"
ao_driver = "alsa"
ao_volnorm = "no"
softvol = "no"
ao_surround = "no"
ao_extra_stereo = "no"
ao_extra_stereo_coefficient = "1.000000"
osd_level = "1"
sub_auto_load = "yes"
sub_unicode = "no"
sub_pos = "100"
sub_overlap = "no"
font_factor = "0.750000"
font_text_scale = "5.000000"
font_osd_scale = "6.000000"
font_blur = "2.000000"
font_outline = "2.000000"
font_autoscale = "3"
cache = "no"
cache_size = "2048"
playbar = "yes"
load_fullscreen = "no"
show_videowin = "yes"
stopxscreensaver = "no"
autosync = "no"
autosync_size = "0"
gui_skin = "default"
gui_save_pos = "yes"
gui_main_pos_x = "643"
gui_main_pos_y = "652"
gui_video_out_pos_x = "326"
gui_video_out_pos_y = "241"
equ_band_00 = "0.000000"
```

thanks!

-steve

---

### Post by Paul41 on 2006-11-04
I haven't used automatix so I don't know if it installed everything for restricted formats. If not this tells you what you need.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by taurus on 2006-11-04
But mplayer still plays even with that warning message, right!!!  If you want to go fullscreen, change the 

```

vo_driver = "x11"
-to-
vo_driver = "xv"

```
in ~/.mplayer/gui.conf.

---

### Post by stevieb on 2006-11-04
that fixed that problem; thanks!

now this comes up:```
Requested audio codec family [mp3] (afm=mp3lib) not available. Enable it at compilation. 
```

After dismissing this message, everything seems to work ok- sound, fullscreen, the works.  can i prevent the message from showing up?

thanks again,

steve

---

### Post by taurus on 2006-11-04
> **stevieb said:**
> 
now this comes up:```
Requested audio codec family [mp3] (afm=mp3lib) not available. Enable it at compilation. 
```

After dismissing this message, everything seems to work ok- sound, fullscreen, the works.  can i prevent the message from showing up?

thanks again,

steve
Yeah.  Download the source and build it yourself with "afm" or "mp3lib" enable...

---

