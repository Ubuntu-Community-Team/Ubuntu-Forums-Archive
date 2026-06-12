---
title: "AVI wont play!!!"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by Niskyspy on 2007-05-14
This is the last things I got to do to completely move from Windows to Linux but I can't seem to make it work.
I have an AVI file that I am trying to open and I get the following messages.
mplayer: Fatal Error: Error opening/initializing the selected video_out (-vo) device 
Totem movie player: An error occurred: Could not determine type of stream

Can someone help me 
Thank you

---

### Post by taurus on 2007-05-14
Edit ~/.mplayer/gui.conf

```
gedit ~/.mplayer/gui.conf
```
and replace whatever driver for video_out to **xv**.  Save it and restart MPlayer again.

---

### Post by Niskyspy on 2007-05-14
Thank you for the fast reply but I cannot find video_out here's what I got

enable_audio_equ = "no"
vo_driver = "xmga"
vo_panscan = "0.000000"
vo_doublebuffering = "yes"
vo_direct_render = "no"
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
gui_main_pos_x = "376"
gui_main_pos_y = "474"
gui_video_out_pos_x = "375"
gui_video_out_pos_y = "110"
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

### Post by kh4nh on 2007-05-14
Open mplayer, right click on the control windows -> Preferences -> Video -> Choose drivers xv or x11

---

### Post by taurus on 2007-05-14
The second line.

```
vo_driver = "**xmga**"
```

---

### Post by Niskyspy on 2007-05-14
it got rid of the error message but still isn't playing any avi files

---

### Post by taurus on 2007-05-14
Which release are you running?  Have you install any codecs for your machine?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Niskyspy on 2007-05-14
7.04 and yes I installed everything I can possibly install

---

### Post by Niskyspy on 2007-05-14
Tried running gxine and got the following error:
The xine engine failed to start
No demuxer found - stream format not recongnized

---

### Post by taurus on 2007-05-14
Have you tried to play that .avi with vlc?  It's available in the repos.

```
sudo aptitude update
sudo aptitude install vlc
vlc **filename.avi**
```

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by Niskyspy on 2007-05-14
Yep, just tried it and it didn't do anything.
The player plays one AVI video (its 800kb video) but when I try to play a movie, the player goes black then turn's back to normal (it has file name written on it and time). When I press play it just sits there and doesn't play anything.

---

### Post by Niskyspy on 2007-05-15
Well, I can't figure this one out, thanks for all your help. 
I think I'll just format my HDD, reinstall the ubuntu and then try to do the same things over again. Because I know more about it now. I think I screwed up some codec somewhere and maybe installed uncomputable codec for this OS. 

If you have any more ideas on how to make it work please post..

Thank you

---

