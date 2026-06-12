---
title: "Help with Mplayer commands"
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by ZeroXR on 2007-02-18
I'm probably confused or something, but I am trying to get Mplayer to run with the GUI interface but I keep getting the "Video Output device not selected" error. The DVD's run properly when I use the command: mplayer dvd://1 -alang en /dev/hdv. When I have tried to use the command: gmplayer dvd://1 -alang en -vo dr /dev/hdc it gives me that error.

Am I using the commands improperly? I'm trying to use the direct rendering option.

Another question, when I am trying to use Mplayer and display subtitles using the syntax command: mplayer dvd://1 -alang en -subcc /dev/hdc, the movie will repeat every second and display the Spanish subtitles and dialogue. Am I incorrectly using the syntax for subtitling? If I am, can anyone clarify on how to use the proper syntax for subtitles?

---

### Post by taurus on 2007-02-18
What does your ~/.mplayer/gui.conf look like anyway?

```
cat ~/.mplayer/gui.conf
```

---

### Post by ZeroXR on 2007-02-19
```
cat ~/.mplayer/gui.conf
```

enable_audio_equ = "no"
vo_driver = "dr"
vo_panscan = "0.000000"
vo_doublebuffering = "yes"
vo_direct_render = "yes"
vo_dxr3_device = "/dev/em8300-0"
v_framedrop = "0"
v_flip = "-1"
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
dvd_device = "/dev/dvd"
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
gui_main_pos_x = "577"
gui_main_pos_y = "569"
gui_video_out_pos_x = "183"
gui_video_out_pos_y = "203"
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

### Post by ZeroXR on 2007-02-19
Anyone..?

Bumped for the Daytime folks 'cause I posted this in the middle of the night.

---

### Post by taurus on 2007-02-19
Edit ~/.mplayer/gui.conf

```
gedit ~/.mplayer/gui.conf
```
and replace the second line from this

```
vo_driver = "dr"
```
to something like this.

```
vo_driver = "xv"
```
Restart gmplayer and see what happens.

---

### Post by ZeroXR on 2007-02-19
That solved my issue with the gmplayer syntax saying it couldn't find the video driver. :)

The next issue that remains a mystery is when I pick english subtitles to test, it seems to repeat every second... and the subtitles are in Spanish. :(

---

### Post by ZeroXR on 2007-02-20
Anyone know anything about the odd subtitles (or closed captioning) bug?

---

